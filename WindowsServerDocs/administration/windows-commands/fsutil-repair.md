---
ms.assetid: 62d77150-1d9e-4069-ab4a-299f33024912
title: Nicht reparieren
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 6e4e285bf8401d628f7e4bcbaeafb0c6defa3ad1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71376912"
---
# <a name="fsutil-repair"></a>Nicht reparieren
>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016, Windows 10, Windows Server 2012 R2, Windows 8.1, Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7

Verwaltet und überwacht die Selbstreparatur Vorgänge von NTFS.

Beispiele für das Verwenden dieses Befehls finden Sie unter [Beispiele](#BKMK_examples).

## <a name="syntax"></a>Syntax

```
fsutil repair [enumerate] <volumepath> [<LogName>]
fsutil repair [initiate] <VolumePath> <FileReference>
fsutil repair [query] <VolumePath>
fsutil repair [set] <VolumePath> <Flags>
fsutil repair [wait][<WaitType>] <VolumePath>

```

## <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|-------------|---------------|
|Auflisten|Listet die entids des Beschädigungs Protokolls eines Volumes auf.|
|\<volumepath >|Gibt das Volume als den Namen des Laufwerks gefolgt von einem Doppelpunkt an.|
|\<logname >|$Corrupt: der Satz bestätigter Beschädigungen auf dem Volume.<br />$Verify: ein Satz potenzieller, nicht überprüfter Beschädigungen auf dem Volume.|
|setzen|Initiiert die Selbstreparatur von NTFS.|
|\<filereferenzierung >|Gibt die NTFS-volumespezifische Datei-ID (Datei Verweis Nummer) an. Der Datei Verweis enthält die Segment Nummer der Datei.|
|query|Fragt den selbst reparierenden Zustand des NTFS-Volumes ab.|
|set|Legt den Selbstheilungs Zustand des Volumes fest.|
|\<flags >|Gibt die zu verwendende Reparaturmethode an, wenn der Selbstreparatur Zustand des Volumes festgelegt wird.<br /><br />Der **Flags** -Parameter kann auf drei Werte festgelegt werden:<br /><br />-   **0x01**: Ermöglicht die allgemeine Reparatur.<br />-   **0x09**: Warnt vor einem möglichen Datenverlust ohne Reparatur.<br />-   **0x00**: Deaktiviert die Reparatur Vorgänge für die Selbstreparatur von NTFS.|
|state|Fragt den Beschädigungs Status des Systems oder für ein bestimmtes Volume ab.|
|Warte|Wartet auf den Abschluss der Reparatur (en). Wenn NTFS auf einem Volume, auf dem es repariert wird, ein Problem festgestellt hat, kann mit dieser Option gewartet werden, bis die Reparatur abgeschlossen ist, bevor ausstehende Skripts ausgeführt werden.|
|[Waittype {0&#124;1}]|Gibt an, ob auf den Abschluss der aktuellen Reparatur gewartet werden soll oder ob auf den Abschluss aller Reparaturen gewartet werden soll. " *Waittype* " kann auf die folgenden Werte festgelegt werden:<br /><br />-   **0**: Wartet, bis alle Reparaturen vollständig sind. (Standardwert)<br />-   **1**: Wartet auf den Abschluss der aktuellen Reparatur.|

## <a name="remarks"></a>Hinweise

-   Die Selbstreparatur von NTFS versucht, die Beschädigungen des NTFS-Dateisystems online zu korrigieren, ohne dass " **Chkdsk. exe** " ausgeführt werden muss. Diese Funktion wurde in Windows Server 2008 eingeführt. Weitere Informationen finden Sie unter [Self-Healing-NTFS](https://go.microsoft.com/fwlink/?LinkID=165401).

## <a name="BKMK_examples"></a>Beispiele

Geben Sie Folgendes ein, um die bestätigten Beschädigungen eines Volumes aufzuzählen:

```
fsutil repair enumerate C: $Corrupt 
```

Geben Sie Folgendes ein, um die Selbstreparatur auf Laufwerk C zu aktivieren:

```
fsutil repair set c: 1
```

Geben Sie Folgendes ein, um die Reparatur der Selbstreparatur auf Laufwerk C zu deaktivieren:

```
fsutil repair set c: 0
```

#### <a name="additional-references"></a>Weitere Verweise
[Erläuterung zur Befehlszeilensyntax](Command-Line-Syntax-Key.md)

[Fsutil](Fsutil.md)

[Selbstreparatur von NTFS](https://go.microsoft.com/fwlink/?LinkID=165401)


