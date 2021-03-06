---
title: Metadaten laden
description: 'Windows-Befehle Thema ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c535487-668b-44fc-babb-ff59cf7d190e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 025f75743d61889c4b987e9a2a575d1c599f04c1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71374621"
---
# <a name="load-metadata"></a>Metadaten laden



Lädt eine Datei "Metadata. cab" vor dem Importieren einer austauschen-Schatten Kopie oder lädt die Writer-Metadaten im Fall einer Wiederherstellung. Bei Verwendung ohne Parameter zeigt die Eingabe **Metadaten** die Hilfe an der Eingabeaufforderung an.

Beispiele für das Verwenden dieses Befehls finden Sie unter [Beispiele](#BKMK_examples).

## <a name="syntax"></a>Syntax

```
load metadata [<Drive>:][<Path>]<MetaData.cab>
```

## <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------|-----------|
|[\<laufwerk >:] [<Path>]|Gibt den Speicherort der Metadatendatei an.|
|Metadaten. cab|Gibt die zu ladende Datei "Metadata. cab" an.|

## <a name="remarks"></a>Hinweise

-   Sie können den **Import** -Befehl verwenden, um eine austauschen-Schatten Kopie auf Grundlage der Metadaten zu importieren, die durch **Laden von Metadaten**angegeben werden.
-   Dieser Befehl wird vor dem Befehl zum **Wiederherstellen von BEGIN** benötigt, um die ausgewählten Writer und Komponenten für die Wiederherstellung zu laden.

## <a name="BKMK_examples"></a>Beispiele

Zum Laden einer Metadatendatei namens "Metafile. cab" aus dem Standard Speicherort geben Sie Folgendes ein:
```
load metadata metafile.cab
```

#### <a name="additional-references"></a>Weitere Verweise

[Erläuterung zur Befehlszeilensyntax](command-line-syntax-key.md)