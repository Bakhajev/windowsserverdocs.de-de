---
title: Ändern des Stammnavigationsverhaltens
description: Entwickeln einer projektmappenerweiterung Windows Admin Center SDK (Project Honolulu)-Ändern des Stamm Navigations Verhaltens
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 08/07/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 78c94f3ea13f54ac31f9de9dd60873b93eba2c17
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385277"
---
# <a name="modify-root-navigation-behavior-for-a-solution-extension"></a>Ändern des Stamm Navigations Verhaltens für eine projektmappenerweiterung

>Gilt für: Windows Admin Center, Windows Admin Center-Vorschau

In dieser Anleitung erfahren Sie, wie Sie das Verhalten der Stamm Navigation für Ihre Lösung ändern, um ein anderes Verbindungs Listen Verhalten zu erhalten, und wie Sie die Liste der Tools ausblenden oder anzeigen.

## <a name="modifying-root-navigation-behavior"></a>Ändern des Verhaltens der Stamm Navigation

Öffnen Sie die Datei "Manifest. JSON" in {Extension root} \src, und suchen Sie die Eigenschaft "rootnavigationbehavior". Diese Eigenschaft hat zwei gültige Werte: "Connections" oder "Path". Das Verhalten "Verbindungen" wird weiter unten in der Dokumentation ausführlich erläutert.

### <a name="setting-path-as-a-rootnavigationbehavior"></a>Festlegen des Pfads als rootnavigationbehavior

Legen Sie den Wert ```rootNavigationBehavior``` auf ```path``` fest, und löschen Sie dann die Eigenschaft ```requirements```, und belassen Sie die ```path```-Eigenschaft als leere Zeichenfolge. Sie haben die minimal erforderliche Konfiguration abgeschlossen, um eine projektmappenerweiterung zu erstellen. Speichern Sie die Datei, und Gulp Build-> Gulp dient als Tool, und laden Sie dann die Erweiterung in die lokale Windows Admin Center-Erweiterung.

Ein gültiges Manifest-entryPoints-Array sieht wie folgt aus:
```
    "entryPoints": [
        {
          "entryPointType": "solution",
          "name": "main",
          "urlName": "testsln",
          "displayName": "resources:strings:displayName",
          "description": "resources:strings:description",
          "icon": "sme-icon:icon-win-powerShell",
          "path": "",
          "rootNavigationBehavior": "path"
        }
    ],
```

Bei Tools, die mit dieser Art von Struktur erstellt werden, sind keine Verbindungen zum Laden erforderlich, aber es sind auch keine Knoten Verbindungsfunktionen vorhanden.

### <a name="setting-connections-as-a-rootnavigationbehavior"></a>Festlegen von Verbindungen als rootnavigationbehavior

Wenn Sie die ```rootNavigationBehavior```-Eigenschaft auf ```connections``` festlegen, wird der Windows Admin Center-Shell mitgeteilt, dass ein verbundener Knoten (immer ein Server eines Typs) vorhanden ist, mit dem eine Verbindung hergestellt werden soll, und der Verbindungsstatus überprüft wird. Dies umfasst zwei Schritte beim Überprüfen der Verbindung. 1) das Windows Admin Center versucht, sich mit Ihren Anmelde Informationen beim Knoten anzumelden (zum Einrichten der PowerShell-Remote Sitzung) und 2) führt das PowerShell-Skript aus, das Sie bereitstellen, um zu ermitteln, ob sich der Knoten in einem Verbindungs fähigen Zustand befindet.

Eine gültige Projektmappendefinition mit Verbindungen sieht wie folgt aus:

``` json
        {
          "entryPointType": "solution",
          "name": "example",
          "urlName": "solutionexample",
          "displayName": "resources:strings:displayName",
          "description": "resources:strings:description",
          "icon": "sme-icon:icon-win-powerShell",
          "rootNavigationBehavior": "connections",
          "connections": {
            "header": "resources:strings:connectionsListHeader",
            "connectionTypes": [
                "msft.sme.connection-type.example"
                ]
            },
            "tools": {
                "enabled": false,
                "defaultTool": "solution"
            }
        },
```

Wenn rootnavigationbehavior auf "Connections" festgelegt ist, müssen Sie die Verbindungs Definition im Manifest erstellen. Dies schließt die Eigenschaft "Header" ein (wird zur Anzeige im projektmappenheader verwendet, wenn ein Benutzer Sie aus dem Menü auswählt), ein connectiontypes-Array (Dadurch wird festgelegt, welche connectiontypes in der Projekt Mappe verwendet werden. Weitere Informationen dazu in der ConnectionProvider-Dokumentation.)

## <a name="enabling-and-disabling-the-tools-menu"></a>Aktivieren und Deaktivieren des Menüs "Extras" ##

Eine weitere in der Projektmappendefinition verfügbare Eigenschaft ist die Eigenschaft "Tools". Dadurch wird festgelegt, ob das Menü Extras und das Tool, das geladen wird, angezeigt werden. Wenn diese Option aktiviert ist, wird das Menü auf der linken Seite des Windows Admin Centers angezeigt. Mit defaulttool ist es erforderlich, dass Sie dem Manifest einen Tool Einstiegspunkt hinzufügen, um die entsprechenden Ressourcen zu laden. Der Wert von "defaulttool" muss die Eigenschaft "Name" des Tools sein, wie er im Manifest definiert ist.
