---
title: Funktionen, die entfernt oder ersetzt, die mit Windows Server, Version 1903 ab
description: Folgendes ist eine Liste der Features und Funktionen in Windows Server, Version 1903 sein, die entweder in, aus dem Produkt entfernt wurden, Version, oder damit begonnen, die für die mögliche Ersetzung in künftigen Versionen berücksichtigt werden. Sie ist für IT-Experten vorgesehen, die Betriebssysteme in einer kommerziellen Umgebung aktualisieren.
ms.prod: windows-server-threshold
ms.technology: server-general
ms.topic: article
ms.date: 05/21/2019
author: jasongerend
ms.author: jgerend
manager: daveba
ms.openlocfilehash: e2f51af55ba7005cb20d8a1c22f6ba9edc20c704
ms.sourcegitcommit: c8cc0b25ba336a2aafaabc92b19fe8faa56be32b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983420"
---
# <a name="features-removed-or-planned-for-replacement-starting-with-windows-server-version-1903"></a>Funktionen, die entfernt oder ersetzt, die mit Windows Server, Version 1903 ab

>Gilt für: Windows Server, version 1903

Folgendes ist eine Liste der Features und Funktionen in Windows Server, Version 1903 sein, die entweder in, aus dem Produkt entfernt wurden, Version, oder damit begonnen, die für die mögliche Ersetzung in künftigen Versionen berücksichtigt werden. Sie ist für IT-Experten vorgesehen, die Betriebssysteme in einer kommerziellen Umgebung aktualisieren. **Diese Liste unterliegt in künftigen Versionen und enthalten möglicherweise nicht alle betroffenen Features oder Funktionen.**

Siehe auch [Funktionen entfernt oder ersetzt, die ab Windows Server-2019](removed-features-19.md).

## <a name="features-were-no-longer-developing"></a>Features, die nicht mehr entwickelt werden

Wir entwickeln diese Funktionen nicht mehr aktiv und kann von einem zukünftigen Update entfernen. Einige Features wurden mit anderen Features oder Funktionen ersetzt, während andere aus verschiedenen Quellen jetzt verfügbar sind. 

Wenn Sie Feedback zu der vorgeschlagenen Austausch diese Features haben, können Sie die [app Feedback-Hub](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)verwenden. 

| Feature | Stattdessen können Sie |
|-----------|---------------------|
|Wi-Fi-WEP und TKIP (**neue**)| Wi-Fi-Netzwerke, die mit älteren WEP und TKIP-Verschlüsselung sind nicht so sicher wie die mithilfe von AES, z. B. WPA2 und WPA3. Unter Windows 10, Version 1903 sein, zeigt eine Verbindung mit einem Netzwerk WEP oder TKIP eine Warnmeldung, dass das Netzwerk nicht sicher ist, aber keine Meldung wird angezeigt, auf Windows Server, Version 1903 sein. In einer zukünftigen Version wird eine Verbindung mit einem Wi-Fi-Netzwerk verwenden diese alten Verschlüsselungen nicht zulässig. Weitere Informationen zu den Sicherheitsrisiken von WEP und TKIP finden Sie in diesem [Blogbeitrag](https://go.microsoft.com/fwlink/p/?linkid=2008426).|
|XDDM-basierte remote-Display-Treibers (**neue**)|Ab dieser Version der Remote Desktop Services basiert verwendet eine Gruppenrichtlinien-Verwaltungskonsole (Windows Display Driver Model, WDDM) indirekte Display Driver (IDD), für eine einzelne Sitzung remote Desktop. Die Unterstützung für Windows 2000 Display Driver Model (XDDM) basierte remote-Anzeigetreiber wird in einer zukünftigen Version entfernt. Unabhängige Softwarehersteller, die XDDM-basierte remote-Display-Treibers verwenden, sollten eine Migration auf das WDDM-Treiber-Modell. Weitere Informationen zum Implementieren von remote-Anzeige indirekte Anzeigetreiber ISVs kann wenden Sie sich an [ rdsdev@microsoft.com ](mailto:rdsdev@microsoft.com).|
|UCS-Protokollerfassungstool (**neue**)|Das UCS-Protokollerfassungstool, während für die Verwendung mit Windows Server nicht explizit vorgesehen wird trotzdem von der Feedback-Hub auf Windows 10 ersetzt.|
|Wichtige Speicherlaufwerk in Hyper-V|Wir arbeiten jedoch nicht mehr auf die Schlüssel Speicherlaufwerk-Funktion in Hyper-V. Wenn Sie VMs der Generation 1 verwenden, sehen Sie sich [Generation 1 VM Virtualisierungssicherheit](https://docs.microsoft.com/windows-server/virtualization/hyper-v/learn-more/generation-1-virtual-machine-security-settings-for-hyper-v) Informationen zu Optionen, die in Zukunft. Wenn Sie neue virtuelle Computer verwenden virtuelle Maschinen der Generation 2 mit TPM-Geräten für eine sicherere Lösung erstellen. |
|Vertrauenswürdige Platform Module (TPM)-Verwaltungskonsole|Die Informationen, die zuvor in der TPM-Verwaltungskonsole zur Verfügung steht jetzt auf die [ **gerätesicherheit** ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-security-center/wdsc-device-security) auf der Seite die [Windows Defender Security Center](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center).|
|Host Guardian Service Active Directory-nachweismodus|Wir nicht mehr Host Guardian Service, Active Directory-nachweismodus entwickeln: Wir haben stattdessen eine neue nachweismodus, hinzugefügt [hosten den schlüsselnachweis](../security/guarded-fabric-shielded-vm/guarded-fabric-create-host-key.md), ist wesentlich einfacher und ebenso als kompatibel ist, als Active Directory-Basis einen Nachweis an.  Dieser neue Modus stellt die entsprechenden Funktionalität mit einer Setupfunktionalität, einfachere Verwaltung und weniger infrastrukturabhängigkeiten als den Nachweis der Active Directory bereit. Host-schlüsselnachweis hat bestehen keine zusätzlichen hardwareanforderungen, über welche Active Directory-Nachweis erforderlich, damit alle vorhandenen Systeme mit den neuen Modus kompatibel bleiben. Finden Sie unter [Bereitstellen von überwachten Hosts](../security/guarded-fabric-shielded-vm/guarded-fabric-configure-hgs-with-authorized-hyper-v-hosts.md) für Weitere Informationen zu den Nachweis-Optionen.|
|OneSync-Dienst|Der Dienst OneSync synchronisiert die Daten für die E-Mail, Kalender und Benutzer-apps. Wir haben die Outlook-app eine Synchronisierungs-Engine hinzugefügt, die die gleiche Synchronisierung bereitstellt.|
|Remote Differential Compression-API-Unterstützung|Remote Differential Compression-API-Unterstützung aktiviert die Synchronisierung von Daten mit einer Remotequelle mit komprimierungstechnologien, die die über das Netzwerk übertragene Datenmenge minimiert. Diese Unterstützung ist nicht aktuell von Microsoft-Produkten verwendet werden.|
|WFP-Erweiterung für einfachen Filter-Switches|Die WFP-Erweiterung für die einfache Filter Switches ermöglicht Entwicklern das Erstellen von [einfaches Netzwerk paketfilterung-Erweiterungen für den virtuellen Hyper-V-Switch](https://docs.microsoft.com/en-us/windows-hardware/drivers/network/using-virtual-switch-filtering). Sie können die gleiche Funktionalität erreichen, durch das Erstellen einer vollständigen filternden-Erweiterungs. Daher müssen wir diese Erweiterung in der Zukunft entfernt.|