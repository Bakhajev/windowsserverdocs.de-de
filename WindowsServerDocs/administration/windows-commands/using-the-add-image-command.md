---
title: Verwenden des Befehls "Add-Image"
description: 'Windows-Befehle Thema ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5b6f4da-90ba-4b0e-9423-66c8ef5172e2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b0d671dd482710c486a6936cdbe3b1cc6b331866
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363737"
---
# <a name="using-the-add-image-command"></a>Verwenden des Befehls "Add-Image"

>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Fügt einem Windows-Bereitstellungsdiensteserver Images hinzu. Beispiele für die Verwendung dieses Befehls finden Sie unter [Beispiele](#BKMK_examples).
## <a name="syntax"></a>Syntax
Verwenden Sie für Start Images die folgende Syntax:
```
wdsutil /add-ImagmediaFile:<wim file path> [/Server:<Server name>mediatype:Boot [/Skipverify] [/Name:<Image name>] [/Description:<Image description>] 
[/Filename:<New wim file name>]
```
Verwenden Sie für Installations Images die folgende Syntax:
```
wdsutil /add-ImagmediaFile:<wim file path>
     [/Server:<Server name>]
   mediatype:Install
     [/Skipverify]
    mediaGroup:<Image group name>]
     [/SingleImage:<Single image name>]
         [/Name:<Name>]
         [/Description:<Description>]
     [/Filename:<File name>]
     [/UnattendFile:<Unattend file path>]
```
## <a name="parameters"></a>Parameter
|Parameter|Beschreibung|
|-------|--------|
mediafile: <. wim-Dateipfad >|Gibt den vollständigen Pfad und den Dateinamen der Windows-Abbild Datei (WIM-Datei) an, die die hinzu zufügenden Bilder enthält.|
|[/Server:<Server name>]|Gibt den Namen des Servers an. Hierbei kann es sich um den NetBIOS-Namen oder den vollqualifizierten Domänennamen (Fully Qualified Domain Name, FQDN) handeln. Wenn Sie keinen Servernamen angeben, wird der lokale Server verwendet.|
MediaType: {Boot&#124;install}|Gibt den Typ der Bilder an, die hinzugefügt werden sollen.|
|[/Skipverify]|Gibt an, dass die Integritäts Überprüfung nicht für die Quell Abbild Datei durchgeführt wird, bevor das Image hinzugefügt wird.|
|[/Name: <Name>]|Legt den anzeigen amen des Bilds fest.|
|/Description<Description>]|Legt die Beschreibung des Bilds fest.|
|[/Filename:<Filename>]|Gibt den neuen Dateinamen für die WIM-Datei an. Auf diese Weise können Sie den Dateinamen der WIM-Datei ändern, wenn Sie das Image hinzufügen. Wenn kein Dateiname angegeben wird, wird der Dateiname des Quell Bilds verwendet. In allen Fällen wird von den Windows-Bereitstellungs Diensten überprüft, ob der Dateiname im Start Abbild Speicher des Ziel Computers eindeutig ist.|
|\mediagroup: <Image group name>]|Gibt den Namen der Abbild Gruppe an, in der die Bilder hinzugefügt werden sollen. Wenn auf dem Server mehr als eine Abbild Gruppe vorhanden ist, muss die Abbild Gruppe angegeben werden. Wenn Sie keine Abbildgruppe angeben und noch keine Abbildgruppe vorhanden ist, wird eine neue erstellt. Andernfalls wird die vorhandene Abbildgruppe verwendet.|
|[/SingleImage: <Single image name>] [/Name: <Name>] /Description<Description>]|Kopiert das angegebene einzelne Bild aus einer WIM-Datei und legt den anzeigen Amen und die Beschreibung des Bilds fest.|
|[/UnattendFile:<Unattend file path>]|Gibt den vollständigen Pfad zur unbeaufsichtigten Installationsdatei an, die den hinzugefügten Images zugeordnet werden soll. Wenn **/SingleImage** nicht angegeben ist, wird die gleiche Datei für die unbeaufsichtigte Installation allen Images in der WIM-Datei zugeordnet.|
## <a name="BKMK_examples"></a>Beispiele
Geben Sie Folgendes ein, um ein Startimage hinzuzufügen:
```
wdsutil /add-ImagmediaFile:"C:\MyFolder\Boot.wimmediatype:Boot
wdsutil /verbose /Progress /add-ImagmediaFile:\\MyServer\Share\Boot.wim /Server:MyWDSServemediatype:Boot /Name:"My WinPE Image" 
/Description:"WinPE Image containing the WDS Client" /Filename:WDSBoot.wim
```
Geben Sie zum Hinzufügen eines Installations Abbilds einen der folgenden Informationen ein:
```
wdsutil /add-ImagmediaFile:"C:\MyFolder\Install.wimmediatype:Install
wdsutil /verbose /Progress /add-ImagmediaFile:\\MyServer\Share \Install.wim /Server:MyWDSServemediatype:InstalmediaGroup:ImageGroup1 
/SingleImage:"Windows Pro" /Name:"My WDS Image"
/Description:"Windows Pro image with Microsoft Office" /Filename:"Win Pro.wim" /UnattendFile:"\\server\share\unattend.xml"
```
#### <a name="additional-references"></a>Weitere Verweise
[Befehlszeilen-Syntax Schlüssel](command-line-syntax-key.md)
 mithilfe des Befehls "[Copy-Image](using-the-copy-image-command.md)" 
 mithilfe des Befehls "[Export-](using-the-export-image-command.md)Image" 
 mithilfe des Befehls "[Get-](using-the-get-image-command.md)Image" 
 mit dem Befehl "[Remove-](using-the-remove-image-command.md)Image" 
 mithilfe[der Replace-Image-Befehl](using-the-replace-image-command.md)1-[Unterbefehl: Set-Image](subcommand-set-image.md)
