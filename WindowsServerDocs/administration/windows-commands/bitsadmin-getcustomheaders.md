---
title: biout admin getcustomheaders
description: 'Thema für Windows-Befehle für **bigsadmin getcustomheaders** : Ruft die benutzerdefinierten HTTP-Header aus dem Auftrag ab.'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f0d38d3-e865-4474-81e8-773d65c3d1cc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 039669fca42803ff22eb4e3d13dfdef5f0a06f93
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381660"
---
# <a name="bitsadmin-getcustomheaders"></a>biout admin getcustomheaders



Ruft die benutzerdefinierten HTTP-Header aus dem Auftrag ab.

## <a name="syntax"></a>Syntax

```
bitsadmin /GetCustomHeaders <Job>
```

## <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------|-----------|
|Auftrag|Der Anzeige Name oder GUID des Auftrags.|

## <a name="BKMK_examples"></a>Beispiele

Im folgenden Beispiel werden die benutzerdefinierten Header für den Auftrag mit dem Namen " *mydownloadjob*" abgerufen.
```
C:\>bitsadmin /GetCustomHeaders myDownloadJob
```

#### <a name="additional-references"></a>Weitere Verweise

[Erläuterung zur Befehlszeilensyntax](command-line-syntax-key.md)