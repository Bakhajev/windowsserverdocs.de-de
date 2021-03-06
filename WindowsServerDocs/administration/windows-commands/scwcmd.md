---
title: scwcmd
description: 'Windows-Befehle Thema ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 188ae881-c7d4-4a7a-b967-8fdc79f5f345
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fae9476f94af5faa6e942239e7d91cf589bb1776
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384259"
---
# <a name="scwcmd"></a>scwcmd

> Gilt für: Windows Server 2012 R2, Windows Server 2012

Das Befehlszeilen Tool scwcmd. exe, das im Sicherheitskonfigurations-Assistenten (Security Configuration Wizard, SCW) enthalten ist, kann zum Ausführen der folgenden Aufgaben verwendet werden:
-   Konfigurieren Sie einen oder mehrere Server mit einer vom SCW generierten Richtlinie.
-   Analysieren Sie einen oder mehrere Server mit einer vom SCW generierten Richtlinie.
-   Anzeigen der Analyseergebnisse im HTML-Format.
-   Zurücksetzen von SCW-Richtlinien
-   Transformieren Sie eine SCW-generierte Richtlinie in systemeigene Dateien, die von Gruppenrichtlinie unterstützt werden.
-   Registrieren Sie eine Sicherheitskonfigurations-Daten Bank Erweiterung mit SCW.

Wenn Sie **scwcmd** verwenden, um eine Richtlinie auf einem Remote Server zu konfigurieren, zu analysieren oder zurückzusetzen, muss SCW auf dem Remote Server installiert sein.

## <a name="syntax"></a>Syntax

```
scwcmd <command> [<subcommand>]
```

## <a name="parameters"></a>Parameter

|Unterbefehl|Beschreibung|
|----------|-----------|
|/analyze|Bestimmt, ob ein Computer mit einer Richtlinie konform ist.</br>Weitere Informationen finden Sie unter [scwcmd: analysieren](scwcmd-analyze.md) für Syntax und Optionen.|
|/configure|Wendet eine vom SCW generierte Sicherheitsrichtlinie auf einen Computer an.</br>Weitere Informationen finden Sie unter [scwcmd: Configure](scwcmd-configure.md) for Syntax and options.|
|/Register|Erweitert oder passt die Sicherheits Konfigurations Datenbank von SCW an, indem eine Sicherheits Konfigurations-Datenbankdatei registriert wird, die Rollen-, Task-, Dienst-oder Port Definitionen enthält.</br>Weitere Informationen finden Sie unter [scwcmd: Register](scwcmd-register.md) für Syntax und Optionen.|
|/rollback|Wendet die neueste Rollback-Richtlinie an und löscht dann diese Rollback-Richtlinie.</br>Weitere Informationen finden Sie unter [scwcmd: Rollback](scwcmd-rollback.md) für Syntax und Optionen.|
|/Transform|Transformiert eine mit SCW generierte Sicherheitsrichtlinien Datei in ein neues Gruppenrichtlinie Objekt (GPO) in Active Directory Domain Services.</br>Weitere Informationen finden Sie unter [scwcmd: Transformieren](scwcmd-transform.md) von Syntax und Optionen.|
|/view|Rendert eine XML-Datei mithilfe einer angegebenen XSL-Transformation.</br>Informationen zur Syntax und zu Optionen finden Sie unter [scwcmd: View](scwcmd-view.md) .|
|/?|Zeigt die Hilfe an der Eingabeaufforderung an.|

#### <a name="additional-references"></a>Weitere Verweise

-   [Erläuterung zur Befehlszeilensyntax](command-line-syntax-key.md)
