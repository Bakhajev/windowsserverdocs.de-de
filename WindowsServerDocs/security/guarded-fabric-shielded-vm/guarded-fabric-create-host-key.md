---
title: Erstellen eines Host Schlüssels und Hinzufügen des Schlüssels zu HGS
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: a12c8494-388c-4523-8d70-df9400bbc2c0
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 2aea6c8416a0f3af04ad6056c5d09a4d07708eaa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71386652"
---
# <a name="create-a-host-key-and-add-it-to-hgs"></a>Erstellen eines Host Schlüssels und Hinzufügen des Schlüssels zu HGS

>Gilt für: Windows Server 2019


In diesem Thema wird beschrieben, wie Hyper-V-Hosts mithilfe des Host Schlüssel Nachweis (Schlüssel Modus) auf geschützte Hosts vorbereitet werden. Erstellen Sie ein Host Schlüsselpaar (oder verwenden Sie ein vorhandenes Zertifikat), und fügen Sie die öffentliche Hälfte des Schlüssels zu HGS hinzu.

## <a name="create-a-host-key"></a>Erstellen eines Host Schlüssels

1.  Installieren Sie Windows Server 2019 auf dem Hyper-V-Host Computer.
2.  Installieren Sie die Hyper-v-und Host-Überwachungsfunktionen von Hyper-v:

    ```powershell
    Install-WindowsFeature Hyper-V, HostGuardian -IncludeManagementTools -Restart
    ``` 

3.  Generieren Sie automatisch einen Host Schlüssel, oder wählen Sie ein vorhandenes Zertifikat aus. Wenn Sie ein benutzerdefiniertes Zertifikat verwenden, sollte es mindestens einen 2048-Bit-RSA-Schlüssel, eine Clientauthentifizierungs-EKU und die Verwendung von digitalen Signatur Schlüsseln aufweisen.

    ```powershell
    Set-HgsClientHostKey
    ```

    Alternativ können Sie einen Fingerabdruck angeben, wenn Sie Ihr eigenes Zertifikat verwenden möchten. 
    Dies kann hilfreich sein, wenn Sie ein Zertifikat für mehrere Computer freigeben möchten, oder wenn Sie ein Zertifikat verwenden möchten, das an ein TPM oder ein HSM gebunden ist. Hier ist ein Beispiel für das Erstellen eines TPM-gebundenen Zertifikats (das verhindert, dass der private Schlüssel gestohlen und auf einem anderen Computer verwendet wird und nur ein TPM 1,2 erforderlich ist):

    ```powershell
    $tpmBoundCert = New-SelfSignedCertificate -Subject “Host Key Attestation ($env:computername)” -Provider “Microsoft Platform Crypto Provider”
    Set-HgsClientHostKey -Thumbprint $tpmBoundCert.Thumbprint
    ```

4.  Holen Sie sich die öffentliche Hälfte des Schlüssels, der für den HGS-Server bereitgestellt werden soll. Sie können das folgende Cmdlet verwenden oder, wenn Sie das Zertifikat an einem anderen Speicherort gespeichert haben, eine CER-Datei mit der öffentlichen Hälfte des Schlüssels bereitstellen. Beachten Sie, dass wir nur den öffentlichen Schlüssel auf HGS speichern und validieren. Wir behalten keine Zertifikat Informationen bei und überprüfen weder die Zertifikatskette noch das Ablaufdatum.

    ```powershell
    Get-HgsClientHostKey -Path "C:\temp\$env:hostname-HostKey.cer"
    ```

5.  Kopieren Sie die CER-Datei auf Ihren HGS-Server.

## <a name="add-the-host-key-to-the-attestation-service"></a>Hinzufügen des Host Schlüssels zum Nachweis Dienst

Dieser Schritt wird auf dem HGS-Server ausgeführt und ermöglicht es dem Host, abgeschirmte VMS auszuführen. Es wird empfohlen, den Namen für den FQDN oder den Ressourcen Bezeichner des Host Computers festzulegen, damit Sie leicht auf den Host, auf dem der Schlüssel installiert ist, verweisen können.

```powershell
Add-HgsAttestationHostKey -Name MyHost01 -Path "C:\temp\MyHost01-HostKey.cer"
``` 

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bestätigen, dass Hosts erfolgreich bestätigen können](guarded-fabric-confirm-hosts-can-attest-successfully.md)

## <a name="see-also"></a>Siehe auch

- [Bereitstellen des Host-Überwachungs Diensts für geschützte Hosts und abgeschirmte VMS](guarded-fabric-deploying-hgs-overview.md)
