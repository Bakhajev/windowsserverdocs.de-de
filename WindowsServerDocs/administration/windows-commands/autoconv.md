---
title: autoconv
description: 'Das Thema "Windows-Befehle" für **autovs** : konvertiert Dateizuordnungs-und FAT32-Volumes in das NTFS-Dateisystem.'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17281e54-0b18-4e84-94ac-24586c82df4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bf36be6bcf3dd8f6c61c6ab0d8780ed77dd8903a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383448"
---
# <a name="autoconv"></a>autoconv

>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

konvertiert Dateizuordnungs-und FAT32-Volumes in das NTFS-Dateisystem, wobei vorhandene Dateien und Verzeichnisse beim Start nach der Ausführung von **Autochk** intakt bleiben. Volumes, die in das NTFS-Dateisystem konvertiert werden, können nicht zurück in FAT oder FAT32 konvertiert werden.
## <a name="remarks"></a>Hinweise
**Autov** kann nicht in der Befehlszeile ausgeführt werden. Diese wird nur beim Start ausgeführt, wenn Sie durch **Convert. exe**festgelegt wird.
## <a name="additional-references"></a>Weitere Verweise
[Befehlszeilen-Syntax Schlüssel](command-line-syntax-key.md)
[Autochk](autochk.md)
[konvertieren](convert.md)von 
[Arbeiten mit Dateisystemen](https://go.microsoft.com/fwlink/?LinkId=4509)
