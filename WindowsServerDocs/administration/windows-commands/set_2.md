---
title: set_2
description: 'Windows-Befehle Thema ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: acf24663-1a50-4321-b48d-1717655e9476
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e91bee5f0d351e461d16ccd22478d67f26887728
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71370913"
---
# <a name="set_2"></a>set_2



Legt den Kontext, die Optionen, den ausführlichen Modus und die Metadatendatei für die Erstellung von Schatten Kopien fest. Wenn Sie ohne Parameter verwendet wird, werden alle aktuellen Einstellungen von **festgelegt** .

## <a name="syntax"></a>Syntax

```
set
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
set verbose {on|off}
set metadata <MetaData.cab>
```

## <a name="set-sub-commands"></a>Unterbefehle festlegen

|Unterbefehl|Beschreibung|
|-----------|-----------|
|Kontext|Legt den Kontext für die Erstellung von Schatten Kopien fest. Siehe [Festlegen des Kontexts](set-context.md) für Syntax und Parameter.|
|Andere|Legt Optionen für die Erstellung von Schatten Kopien fest. Informationen finden Sie unter [Set-Option](set-option.md) für Syntax und Parameter.|
|Ausführlich|Schaltet den ausführlichen Ausgabemodus ein oder aus. Weitere Informationen zu Syntax und Parametern finden Sie unter [Set ausführliche](set-verbose.md) .|
|Benötigten|Legt den Namen und den Speicherort der Metadatendatei für die Schatten Erstellung fest. Informationen zu Syntax und Parametern finden Sie unter [Set Metadata](set-metadata.md) .|
|/?|Zeigt die Hilfe an der Eingabeaufforderung an.|

#### <a name="additional-references"></a>Weitere Verweise

[Erläuterung zur Befehlszeilensyntax](command-line-syntax-key.md)