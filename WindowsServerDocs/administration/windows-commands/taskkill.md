---
title: taskkill
description: 'Windows-Befehle Thema ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2b71e792-08b6-46d4-95a5-cb6336a79524
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 21aec17c649960daffd1aeba80d4448bb9d0ecf7
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383658"
---
# <a name="taskkill"></a>taskkill

>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Beendet eine oder mehrere Aufgaben oder Prozesse. Prozesse können nach Prozess-ID oder Imagename beendet werden. **taskkill** ersetzt das **Kill** -Tool.
Beispiele für das Verwenden dieses Befehls finden Sie unter [Beispiele](#examples).

## <a name="syntax"></a>Syntax

```
taskkill [/s <computer> [/u [<Domain>\]<UserName> [/p [<Password>]]]] {[/fi <Filter>] [...] [/pid <ProcessID> | /im <ImageName>]} [/f] [/t]
```

## <a name="parameters"></a>Parameter

|         Parameter         |                                                                                                                                        Beschreibung                                                                                                                                        |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      /s \<Computer >       |                                                                                    Gibt den Namen oder die IP-Adresse eines Remote Computers an (verwenden Sie keine umgekehrten Schrägstriche). Der Standardwert ist der lokale Computer.                                                                                     |
| /u \<Domäne >\\Benutzername>\< | Führt den Befehl mit den Konto Berechtigungen des Benutzers aus, der durch *Benutzername* oder *Domäne*\\*Benutzername*angegeben ist. **/u** kann nur angegeben werden, wenn **/s** angegeben wird. Der Standardwert sind die Berechtigungen des Benutzers, der zurzeit an dem Computer angemeldet ist, der den Befehl ausgibt. |
|      /p \<Password >       |                                                                                                   Gibt das Kennwort des Benutzerkontos an, das im **/u** -Parameter angegeben ist.                                                                                                   |
|       /fi \<filtern >       |          Wendet einen Filter an, um einen Satz von Tasks auszuwählen. Sie können mehr als einen Filter verwenden oder das Platzhalter Zeichen ( **\\** \*) verwenden, um alle Aufgaben oder Bildnamen anzugeben. [Gültige Filternamen](#filter-names-operators-and-values), Operatoren und Werte finden Sie in der folgenden Tabelle.           |
|     /PID \<ProcessID >     |                                                                                                                 Gibt die Prozess-ID des Prozesses an, der beendet werden soll.                                                                                                                 |
|     /im-Befehl \<ImageName >      |                                                                                Gibt den Bildnamen des Prozesses an, der beendet werden soll. Verwenden Sie das Platzhalter **\\** Zeichen (\*), um alle Bildnamen anzugeben.                                                                                |
|            /f             |                                                                    Gibt an, dass Prozesse erzwungen werden. Dieser Parameter wird bei Remote Prozessen ignoriert. Alle Remote Prozesse werden erzwungen.                                                                     |
|            /t             |                                                                                                          Beendet den angegebenen Prozess und alle von ihm gestarteten untergeordneten Prozesse.                                                                                                          |

#### <a name="filter-names-operators-and-values"></a>Filter Namen, Operatoren und Werte

| Filter Name |    Gültige Operatoren     |                                                                Gültiger Wert (e)                                                                |
|-------------|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
|   STANDS    |         eq, ne         |                                                 AUSFÜHREN &#124; VON NICHT &#124; REAGIERENDEM UNBEKANNTER                                                 |
|  IMAGENAME  |         eq, ne         |                                                                  Bildname                                                                  |
|     PID     | eq, ne, gt, lt, ge, le |                                                                  PID-Wert                                                                   |
|   SITZUNG   | eq, ne, gt, lt, ge, le |                                                                Sitzungsnummer                                                                |
|   CpuTime   | eq, ne, gt, lt, ge, le | CPU-Zeit im Format <em>HH</em> **:** <em>mm</em> **:** <em>SS</em>, wobei *mm* und *SS* zwischen 0 und 59 liegen und *HH* eine beliebige Zahl ohne Vorzeichen ist. |
|  MEMUSAGE   | eq, ne, gt, lt, ge, le |                                                              Speicherauslastung in KB                                                              |
|  USER   |         eq, ne         |                                               Gültiger Benutzername (*Benutzer* oder *Domänen*\\*Benutzer*)                                               |
|  BETREUUNG   |         eq, ne         |                                                                 Dienstname                                                                 |
| WINDOWTITLE |         eq, ne         |                                                                 Fenstertitel                                                                 |
|   MODULEN   |         eq, ne         |                                                                   DLL-Name                                                                   |

## <a name="remarks"></a>Hinweise
* Die Filter WindowTitle und Status werden nicht unterstützt, wenn ein Remote System angegeben wird.
* Das Platzhalter Zeichen **\\** (<em>) wird nur für die Option * */im-Befehl</em> akzeptiert* , wenn ein Filter angewendet wird.
* Die Beendigung von Remote Prozessen wird immer erzwungen, unabhängig davon, ob die **/f** -Option angegeben ist.
* Wenn Sie einen Computernamen für den Host Namen Filter bereitstellen, wird ein Herunterfahren ausgelöst, und alle Prozesse werden beendet.
* Sie können **tasklist** verwenden, um die Prozess-ID (PID) für die Beendigung des Prozesses zu bestimmen.

## <a name="examples"></a>Beispiele

Um die Prozesse mit den Prozess-IDs 1230, 1241 und 1253 zu beenden, geben Sie Folgendes ein:

```
taskkill /pid 1230 /pid 1241 /pid 1253
```

Geben Sie Folgendes ein, um den Prozess "Notepad. exe" zu beenden, wenn er vom System gestartet wurde:

```
taskkill /f /fi "USERNAME eq NT AUTHORITY\SYSTEM" /im notepad.exe
```

Um alle Prozesse auf dem Remote Computer "srvmain" mit einem Image Namen zu beenden, der mit "Hinweis" beginnt, geben Sie bei Verwendung der Anmelde Informationen für das Benutzerkonto "hiropln" Folgendes ein:

```
taskkill /s srvmain /u maindom\hiropln /p p@ssW23 /fi "IMAGENAME eq note*" /im *
```

Um den Prozess mit der Prozess-ID 2134 und allen untergeordneten Prozessen zu beenden, die gestartet wurden, aber nur, wenn diese Prozesse vom Administrator Konto gestartet wurden, geben Sie Folgendes ein:

```
taskkill /pid 2134 /t /fi "username eq administrator"
```

Um alle Prozesse zu beenden, die eine Prozess-ID haben, die größer oder gleich 1000 ist, unabhängig von Ihren Image Namen, geben Sie Folgendes ein:

```
taskkill /f /fi "PID ge 1000" /im *
```

#### <a name="additional-references"></a>Weitere Verweise
[Erläuterung zur Befehlszeilensyntax](command-line-syntax-key.md)
