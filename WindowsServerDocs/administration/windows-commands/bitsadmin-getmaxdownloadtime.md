---
title: BI-admin getmaxdownloadtime
description: 'Thema Windows-Befehle für **bistiadmin getmaxdownloadtime** : Ruft das Download Timeout in Sekunden ab.'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdce64f6-7125-489d-be3c-4af1dfc8c46a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 39a19f86e97c1a525b5beb0c5f3b23dff349cb19
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71381579"
---
# <a name="bitsadmin-getmaxdownloadtime"></a>BI-admin getmaxdownloadtime

>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Ruft das Download Timeout in Sekunden ab.

## <a name="syntax"></a>Syntax

```
bitsadmin /GetMaxDownloadtime <Job> 
```

## <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|-------|--------|
|Auftrag|Der Anzeige Name oder GUID des Auftrags.|

## <a name="remarks"></a>Hinweise

-   N\/A

## <a name="BKMK_examples"></a>Beispiele
Im folgenden Beispiel wird die maximale Downloadzeit für den Auftrag mit dem Namen *mydownloadjob* in Sekunden abgerufen.

```
C:\>bitsadmin /GetMaxDownloadtime myDownloadJob
```

## <a name="additional-references"></a>Weitere Verweise
[Erläuterung zur Befehlszeilensyntax](command-line-syntax-key.md)


