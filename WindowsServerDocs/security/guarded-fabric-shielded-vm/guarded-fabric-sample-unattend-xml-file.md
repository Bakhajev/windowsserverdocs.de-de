---
title: Erstellen einer Antwortdatei für die BS-Spezialisierung
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: 299aa38e-28d2-4cbe-af16-5b8c533eba1f
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 4920f9a90bd0190d390a9d35b3d265023d69efac
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386504"
---
# <a name="create-os-specialization-answer-file"></a>Erstellen einer Antwortdatei für die BS-Spezialisierung

>Gilt für: Windows Server 2019, Windows Server (halbjährlicher Kanal), Windows Server 2016

Zur Vorbereitung der Bereitstellung von abgeschirmten VMS müssen Sie möglicherweise eine Antwortdatei für die Betriebssystem Spezialisierung erstellen. Unter Windows wird dies häufig als die Datei "Unattend. xml" bezeichnet. Die Windows PowerShell-Funktion **New-shieldingdatabeantworsdatei** unterstützt Sie dabei. Anschließend können Sie die Antwortdatei verwenden, wenn Sie abgeschirmte VMS mithilfe System Center Virtual Machine Manager (oder einer anderen Fabric Controller) aus einer Vorlage erstellen.

Allgemeine Richtlinien für Dateien für die unbeaufsichtigte Installation für abgeschirmte VMS finden Sie unter [Erstellen einer Antwortdatei](guarded-fabric-tenant-creates-shielding-data.md#create-an-answer-file).
 
## <a name="downloading-the-new-shieldingdataanswerfile-function"></a>Herunterladen der New-shieldingdatabeantworfile-Funktion

Sie können die Funktion **New-shieldingdatabeantworsdatei** aus dem [PowerShell-Katalog](https://aka.ms/gftools)abrufen. Wenn Ihr Computer über eine Internet Verbindung verfügt, können Sie ihn mit dem folgenden Befehl aus PowerShell installieren:

```powershell
Install-Module GuardedFabricTools -Repository PSGallery -MinimumVersion 1.0.0
```

Die `unattend.xml`-Ausgabe kann zusammen mit zusätzlichen Artefakten in die Schutz Daten gepackt werden, damit Sie zum Erstellen von abgeschirmten VMS aus Vorlagen verwendet werden kann.

In den folgenden Abschnitten wird gezeigt, wie Sie die Funktionsparameter für eine `unattend.xml`-Datei mit verschiedenen Optionen verwenden können:

- [Grundlegende Windows-Antwortdatei](#basic-windows-answer-file)
- [Windows-Antwortdatei mit Domänen Beitritt](#windows-answer-file-with-domain-join)
- [Windows-Antwortdatei mit statischen IPv4-Adressen](#windows-answer-file-with-static-ipv4-addresses)
- [Windows-Antwortdatei mit einem benutzerdefinierten Gebiets Schema](#windows-answer-file-with-a-custom-locale)
- [Grundlegende Linux-Antwortdatei](#basic-linux-answer-file)

## <a name="basic-windows-answer-file"></a>Grundlegende Windows-Antwortdatei

Mit den folgenden Befehlen wird eine Windows-Antwortdatei erstellt, die einfach das Kennwort des Administrator Kontos und den Hostnamen festlegt.
Die VM-Netzwerkadapter verwenden DHCP zum Abrufen von IP-Adressen, und der virtuelle Computer wird nicht zu einer Active Directory Domäne hinzugefügt.
Wenn Sie zur Eingabe von Administrator Anmelde Informationen aufgefordert werden, geben Sie den gewünschten Benutzernamen und das Kennwort an.
Verwenden Sie "Administrator" als Benutzername, wenn Sie das integrierte Administrator Konto konfigurieren möchten.

```powershell
$adminCred = Get-Credential -Message "Local administrator account"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred
```

## <a name="windows-answer-file-with-domain-join"></a>Windows-Antwortdatei mit Domänen Beitritt

Mit den folgenden Befehlen wird eine Windows-Antwortdatei erstellt, die den abgeschirmten virtuellen Computer mit einer Active Directory Domäne verbindet.
Die VM-Netzwerkadapter verwenden DHCP zum Abrufen von IP-Adressen.

Bei der ersten Eingabeaufforderung werden die Informationen zum lokalen Administrator Konto angefordert.
Verwenden Sie "Administrator" als Benutzername, wenn Sie das integrierte Administrator Konto konfigurieren möchten.

Die zweite Eingabeaufforderung fordert Anmelde Informationen an, die über das Recht verfügen, den Computer mit der Active Directory Domäne zu verknüpfen.

Stellen Sie sicher, dass Sie den Wert des Parameters "-Domain Name" in den voll qualifizierten Domänen Namen (FQDN) Ihrer Active Directory Domäne ändern.

```powershell
$adminCred = Get-Credential -Message "Local administrator account"
$domainCred = Get-Credential -Message "Domain join credentials"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred -DomainName 'my.contoso.com' -DomainJoinCredentials $domainCred
```
## <a name="windows-answer-file-with-static-ipv4-addresses"></a>Windows-Antwortdatei mit statischen IPv4-Adressen

Die folgenden Befehle erstellen eine Windows-Antwortdatei, die statische IP-Adressen verwendet, die während der Bereitstellung vom Fabric-Manager bereitgestellt werden, z. b. System Center Virtual Machine Manager

Virtual Machine Manager stellt mithilfe eines IP-Pools drei Komponenten für die statische IP-Adresse bereit: IPv4-Adresse, IPv6-Adresse, Gatewayadresse und DNS-Adresse. Wenn Sie möchten, dass zusätzliche Felder eingeschlossen werden oder eine benutzerdefinierte Netzwerkkonfiguration erforderlich ist, müssen Sie die vom Skript erstellte Antwortdatei manuell bearbeiten.

Die folgenden Screenshots zeigen die IP-Adress Pools, die Sie in Virtual Machine Manager konfigurieren können. Diese Pools sind erforderlich, wenn Sie statische IP-Adressen verwenden möchten.

Derzeit unterstützt die Funktion nur einen DNS-Server. Ihre DNS-Einstellungen würden wie folgt aussehen:

![Konfigurieren des DNS-Servers mit statischem IP-Pool](../media/Guarded-Fabric-Shielded-VM/guarded-host-unattend-static-ip-address-pool-dns-settings.png)

Im folgenden finden Sie eine Zusammenfassung zum Erstellen des statischen IP-Adress Pools. Kurz gesagt, Sie benötigen nur eine Netzwerk Route, ein Gateway und einen DNS-Server, und Sie müssen Ihre IP-Adresse angeben.

![Zusammenfassung der Erstellung statischer IP-Pools](../media/Guarded-Fabric-Shielded-VM/guarded-host-unattend-static-ip-address-pool-summary.png)

Sie müssen Ihren Netzwerkadapter für den virtuellen Computer konfigurieren. Der folgende Screenshot zeigt, wo Sie diese Konfiguration festlegen können und wie Sie Sie in statische IP-Adressen wechseln.

![Konfigurieren der Hardware zur Verwendung statischer IP-Adressen](../media/Guarded-Fabric-Shielded-VM/guarded-host-unattend-static-ip-address-pool-network-adapter-settings.png)

Anschließend können Sie den `-StaticIPPool`-Parameter verwenden, um die statischen IP-Elemente in die Antwortdatei einzuschließen. Die Parameter `@IPAddr-1@`, `@NextHop-1-1@` und `@DNSAddr-1-1@` in der Antwortdatei werden dann durch die tatsächlichen Werte ersetzt, die Sie zum Zeitpunkt der Bereitstellung in Virtual Machine Manager angegeben haben.

```powershell
$adminCred = Get-Credential -Message "Local administrator account"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred -StaticIPPool IPv4Address
```

## <a name="windows-answer-file-with-a-custom-locale"></a>Windows-Antwortdatei mit einem benutzerdefinierten Gebiets Schema

Mit den folgenden Befehlen wird eine Windows-Antwortdatei mit einem benutzerdefinierten Gebiets Schema erstellt.

Wenn Sie zur Eingabe von Administrator Anmelde Informationen aufgefordert werden, geben Sie den gewünschten Benutzernamen und das Kennwort an.
Verwenden Sie "Administrator" als Benutzername, wenn Sie das integrierte Administrator Konto konfigurieren möchten.

```powershell
$adminCred = Get-Credential -Message "Local administrator account"
$domainCred = Get-Credential -Message "Domain join credentials"

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -AdminCredentials $adminCred -Locale es-ES
```

## <a name="basic-linux-answer-file"></a>Grundlegende Linux-Antwortdatei

Ab Windows Server, Version 1709, können Sie bestimmte Linux-Gast Betriebssysteme auf abgeschirmten VMS ausführen.
Wenn Sie den System Center Virtual Machine Manager Linux-Agent verwenden, um diese VMS zu spezialisieren, kann das Cmdlet New-shieldingdatabeantworsdatei kompatible Antwort Dateien für das Cmdlet erstellen.

In einer Linux-Antwortdatei enthalten Sie in der Regel das Stamm Kennwort, den Stamm-SSH-Schlüssel und optional Informationen zum statischen IP-Pool.
Ersetzen Sie den Pfad zur öffentlichen Hälfte Ihres SSH-Schlüssels, bevor Sie das folgende Skript ausführen.

```powershell
$rootPassword = Read-Host -Prompt "Root password" -AsSecureString

New-ShieldingDataAnswerFile -Path '.\ShieldedVMAnswerFile.xml' -RootPassword $rootPassword -RootSshKey '~\.ssh\id_rsa.pub'
```

## <a name="see-also"></a>Siehe auch

- [Bereitstellen von abgeschirmten VMs](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)
- [Geschütztes Fabric und abgeschirmte VMs](guarded-fabric-and-shielded-vms-top-node.md)
