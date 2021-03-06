---
title: bcdedit
description: 'Windows-Befehls Thema für **Bcdedit** : Erstellen neuer Speicher, Ändern vorhandener Speicher und Hinzufügen von Start Menü Parametern.'
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab2da47d-3aac-44a0-b7fd-bd9561d61553
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/27/2018
ms.openlocfilehash: 9448f4461a089a93382ef8cd9e804b382fca27e4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71382246"
---
# <a name="bcdedit"></a>bcdedit



Startkonfigurationsdaten (BCD)-Dateien stellen einen Speicher bereit, der zum Beschreiben von Start Anwendungen und Start Anwendungseinstellungen verwendet wird. Die Objekte und Elemente im Speicher ersetzen "Boot. ini".

BCDEdit ist ein Befehlszeilen Tool zum Verwalten von BCD-Speichern. Sie kann für eine Vielzahl von Zwecken verwendet werden, einschließlich der Erstellung neuer Speicher, der Änderung vorhandener Speicher, dem Hinzufügen von Start Menü Parametern usw. Bcdedit bietet im Wesentlichen denselben Zweck wie "Bootcfg. exe" in früheren Versionen von Windows, jedoch mit zwei wesentlichen Verbesserungen:
-   Macht einen breiteren Bereich von Start Parametern verfügbar als "Bootcfg. exe".
-   Bietet verbesserte Skriptunterstützung.

> [!NOTE]
> Administratorrechte sind erforderlich, um BCD mit bcdedit zu ändern.

BCDEdit ist das primäre Tool zum Bearbeiten der Startkonfiguration von Windows Vista und höheren Versionen von Windows. Es ist in der Windows Vista-Distribution im Ordner%windir%\system32 enthalten.

BCDEdit ist auf die Standard Datentypen beschränkt und wurde hauptsächlich für die Durchführung einzelner allgemeiner Änderungen an BCD entworfen. Bei komplexeren Vorgängen oder nicht standardmäßigen Datentypen können Sie die BCD-Windows-Verwaltungsinstrumentation (WMI)-API (Application Programming Interface) verwenden, um leistungsfähigere und flexiblere benutzerdefinierte Tools zu erstellen.

## <a name="syntax"></a>Syntax

```
BCDEdit /Command [<Argument1>] [<Argument2>] ...
```

## <a name="parameters"></a>Parameter

### <a name="general-bcdedit-command-line-option"></a>Allgemeine bcdedit-Befehlszeilen Option

|Option|Beschreibung|
|------|-----------|
|/?|Zeigt eine Liste der bcdedit-Befehle an. Wenn Sie diesen Befehl ohne ein Argument ausführen, wird eine Zusammenfassung der verfügbaren Befehle angezeigt. Führen Sie **Bcdedit/?** aus, um die ausführliche Hilfe zu einem bestimmten Befehl anzuzeigen. \<command >, wobei <command> der Name des Befehls ist, zu dem Sie nach weiteren Informationen suchen. Beispielsweise zeigt **Bcdedit/?-erstellungsore** eine ausführliche Hilfe zum Befehl "featestore" an.|

### <a name="parameters-that-operate-on-a-store"></a>Parameter, die in einem Speicher betrieben werden

|Option|Beschreibung|
|------|-----------|
|/createstore|Erstellt einen neuen leeren Start Konfigurationsdaten Speicher. Der erstellte Speicher ist kein Systemspeicher.|
|/Export|Exportiert den Inhalt des System Stores in eine Datei. Diese Datei kann später verwendet werden, um den Status des System Stores wiederherzustellen. Dieser Befehl ist nur für den Systemspeicher gültig.|
|/Import|Stellt den Status des System Stores mithilfe einer Sicherungs Datendatei wieder her, die zuvor mit der **/Export** -Option generiert wurde. Mit diesem Befehl werden alle vorhandenen Einträge im Systemspeicher gelöscht, bevor der Import Vorgang durchgeführt wird. Dieser Befehl ist nur für den Systemspeicher gültig.|
|/Store|Diese Option kann mit den meisten Bcdedit-Befehlen verwendet werden, um den zu verwendenden Speicher anzugeben. Wenn diese Option nicht angegeben ist, arbeitet bcdedit im Systemspeicher. Das Ausführen des Befehls **bcdedit/store** mit sich selbst entspricht dem Ausführen des Befehls **bcdedit/enum Active** .|

### <a name="parameters-that-operate-on-entries-in-a-store"></a>Parameter, die für Einträge in einem Speicher ausgeführt werden

|Parameter|Beschreibung|
|---------|-----------|
|/Copy|Erstellt eine Kopie eines angegebenen Start Eintrags in demselben Systemspeicher.|
|/Create|Erstellt einen neuen Eintrag im Datenspeicher für die Startkonfiguration. Wenn ein bekannter Bezeichner angegeben wird, können die Parameter **/Anwendungs-** , **/inherit**und **/Device** nicht angegeben werden. Wenn ein Bezeichner nicht angegeben oder nicht bekannt ist, muss eine **/Anwendungs-** -, **/inherit**-oder **/Device** -Option angegeben werden.|
|/delete|Löscht ein Element aus einem angegebenen Eintrag.|

### <a name="parameters-that-operate-on-entry-options"></a>Parameter, die mit Eingabeoptionen arbeiten

|Parameter|Beschreibung|
|---------|-----------|
|/deletevalue|Löscht ein angegebenes Element aus einem Start Eintrag.|
|/Set|Legt einen Einstiegs Optionswert fest.|

### <a name="parameters-that-control-output"></a>Parameter, die die Ausgabe steuern

|Parameter|Beschreibung|
|---------|-----------|
|/Enum|Listet Einträge in einem Speicher auf. Die **/enum** -Option ist der Standardwert für bcedit, sodass das Ausführen des **Bcdedit** -Befehls ohne Parameter dem Ausführen des Befehls **bcdedit/enum Active** entspricht.|
|/v|Ausführliche-Modus. Üblicherweise werden alle bekannten Eintrags Bezeichner durch ihre benutzerfreundliche Kurzform dargestellt. Wenn Sie **/v** als Befehlszeilenoption angeben, werden alle Bezeichner vollständig angezeigt. Das Ausführen des Befehls **Bcdedit/v** mit sich selbst entspricht dem Ausführen des Befehls **bcdedit/enum Active/v** .|

### <a name="parameters-that-control-the-boot-manager"></a>Parameter zum Steuern des Start-Managers

|Parameter|Beschreibung|
|---------|-----------|
|/bootsequence|Gibt eine einmalige Anzeigereihenfolge an, die für den nächsten Start verwendet werden soll. Dieser Befehl ähnelt der **/displayorder** -Option, mit dem Unterschied, dass er nur beim nächsten Start des Computers verwendet wird. Anschließend wird der Computer auf die ursprüngliche Anzeigereihenfolge zurückgesetzt.|
|/Standard:|Gibt den Standardeintrag an, den der Start-Manager auswählt, wenn das Timeout abläuft.|
|/displayorder|Gibt die Anzeigereihenfolge an, die der Start-Manager beim Anzeigen von Start Parametern für einen Benutzer verwendet.|
|/Timeout|Gibt die Wartezeit in Sekunden an, bevor der Start-Manager den Standardeintrag auswählt.|
|/toolsdisplayorder|Gibt die Anzeigereihenfolge für den Start-Manager an, **die beim Anzeigen des Menüs Extras** verwendet werden soll.|

### <a name="parameters-that-control-emergency-management-services"></a>Parameter zur Steuerung der Notfall Verwaltungsdienste

|Parameter|Beschreibung|
|---------|-----------|
|/bootems|Aktiviert oder deaktiviert die Notfall Verwaltungsdienste (EMS) für den angegebenen Eintrag.|
|/ems|Aktiviert oder deaktiviert EMS für den angegebenen Betriebssystem-Start Eintrag.|
|/emssettings|Legt die globalen EMS-Einstellungen für den Computer fest. **/Emssettings** aktiviert oder deaktiviert EMS nicht für einen bestimmten Start Eintrag.|

### <a name="parameters-that-control-debugging"></a>Parameter zum Steuern des Debuggens

|Parameter|Beschreibung|
|---------|-----------|
|/bootdebug|Aktiviert oder deaktiviert den Start Debugger für einen angegebenen Start Eintrag. Obwohl dieser Befehl für jeden Start Eintrag funktioniert, ist er nur für Start Anwendungen wirksam.|
|/dbgsettings|Gibt die globalen Debuggereinstellungen für das System an oder zeigt diese an. Mit diesem Befehl wird der Kernel Debugger weder aktiviert noch deaktiviert. Verwenden Sie hierfür die Option **/Debug** . Verwenden Sie zum Festlegen einer einzelnen globalen Debuggereinstellung das **bcdedit/set** \<dbgsettings-> <type>. <value> -Befehl abgerufen wird.|
|/debug|Aktiviert oder deaktiviert den Kernel Debugger für einen angegebenen Start Eintrag.|

## <a name="examples"></a>Beispiele

Beispiele für BCDEdit finden Sie in der [Referenz zu Bcdedit-Optionen](https://docs.microsoft.com/windows-hardware/drivers/devtest/bcd-boot-options-reference).