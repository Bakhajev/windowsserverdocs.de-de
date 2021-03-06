---
title: Online-Datenträger
description: 'Windows-Befehle Thema ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc44a783-eaa4-40ca-be01-5703b5bf4eb3
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3d798bf34ec2f9d2f01b5470c4ec52f936674135
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372510"
---
# <a name="online-disk"></a>Online-Datenträger



Schaltet Datenträger, die derzeit offline sind, in einen Online Status.

> [!IMPORTANT]
> Dieser Befehl ist in keiner Edition von Windows Vista verfügbar.

> [!IMPORTANT]
> Dieser Befehl schlägt fehl, wenn er auf einem schreibgeschützten Datenträger verwendet wird.

Anweisungen zur Verwendung dieses Befehls finden Sie unter [Reaktivieren eines fehlenden oder offline](https://go.microsoft.com/fwlink/?LinkId=207046) geschalteten dynamischen Datenträgers (https://go.microsoft.com/fwlink/?LinkId=207046).

## <a name="syntax"></a>Syntax

```
online disk [noerr]
```

## <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------|-----------|
|Noerr|Nur für Skripterstellung. Wenn ein Fehler auftritt, verarbeitet DiskPart weiterhin Befehle so, als ob der Fehler nicht aufgetreten ist. Ohne diesen Parameter bewirkt ein Fehler, dass DiskPart mit einem Fehlercode beendet wird.|

## <a name="remarks"></a>Hinweise

-   Bei Verwendung ohne Parameter in Windows Vista wird mit diesem Befehl eine Datenträger Gruppe verwendet. Für Basis Datenträger gibt es nie mehr als einen Datenträger pro Gruppe. Bei dynamischen Datenträgern umfasst die Gruppe alle nicht-fremden dynamischen Datenträger.
-   Bei Basis Datenträgern versucht dieser Befehl, den ausgewählten Datenträger und alle Volumes auf diesem Datenträger online zu schalten.
-   Bei dynamischen Datenträgern wird mit diesem Befehl versucht, alle Datenträger online zu schalten, die auf dem lokalen Computer nicht als fremd gekennzeichnet sind. Außerdem wird versucht, alle Volumes auf dem Satz dynamischer Datenträger online zu schalten.
-   Wenn ein dynamischer Datenträger in einer Datenträger Gruppe online geschaltet wird und es sich um den einzigen Datenträger in der Gruppe handelt, wird die ursprüngliche Gruppe neu erstellt, und der Datenträger wird in diese Gruppe verschoben. Wenn die Gruppe andere Datenträger enthält und Sie online sind, wird der Datenträger einfach wieder der Gruppe hinzugefügt.
-   Wenn die Gruppe eines ausgewählten Datenträgers gespiegelte oder RAID-5-Volumes enthält, werden diese Volumes von diesem Befehl ebenfalls neu synchronisiert.
-   Ein Datenträger muss ausgewählt werden, damit dieser Befehl erfolgreich ausgeführt werden konnte. Wählen Sie mit dem Befehl Datenträger **auswählen** einen Datenträger aus, und verschieben Sie den Fokus auf den Datenträger.

## <a name="BKMK_examples"></a>Beispiele

Geben Sie Folgendes ein, um den Datenträger online zu schalten:
```
online disk
```

#### <a name="additional-references"></a>Weitere Verweise

[Erläuterung zur Befehlszeilensyntax](command-line-syntax-key.md)

