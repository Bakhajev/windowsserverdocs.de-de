---
title: Dateiverwaltungsaufgaben
description: Dieser Artikel beschreibt das Automatisieren von Dateiverwaltungsaufgaben
ms.date: 7/7/2017
ms.prod: windows-server
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 257ee2955c4f521d14f01ec197fd45e5194eef02
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71394104"
---
# <a name="file-management-tasks"></a>Dateiverwaltungsaufgaben

> Gilt für: Windows Server 2019, Windows Server 2016, Windows Server (halbjährlicher Kanal), Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Dateiverwaltungsaufgaben automatisieren die Suche nach Teilmengen von Dateien auf einem Server und das Anwenden von einfachen Befehlen. Diese Aufgaben können so geplant werden, dass sie automatisch in regelmäßigen Abständen ausgeführt werden, um sich wiederholende Kosten zu senken. Dateien, die durch eine Dateiverwaltungsaufgabe verarbeitet werden, können über folgende Eigenschaften festgelegt werden:

-   Speicherort
-   Klassifizierungseigenschaften
-   Erstellungszeit
-   Zeitpunkt der Änderung
-   Zeitpunkt des letzten Zugriffs

Dateiverwaltungsaufgaben können auch konfiguriert werden, um Dateibesitzer über alle bevorstehenden Richtlinien zu benachrichtigen, die auf ihre Dateien angewendet werden.

> [!Note]
> Einzelne Dateiverwaltungsaufgaben werden unabhängig von Zeitplänen ausgeführt.

<br />
In diesem Abschnitt werden folgende Themen behandelt:

-   [Erstellen einer Dateiablaufaufgabe](create-file-expiration-task.md)
-   [Erstellen einer benutzerdefinierten Dateiverwaltungsaufgabe](create-custom-file-management-task.md)

> [!Note]
> Zum Festlegen von E-Mail-Benachrichtigungen und bestimmten Berichtsfunktionen müssen Sie zuerst die Optionen des Ressourcen-Manager für Dateiserverkonfigurieren konfigurieren.

## <a name="see-also"></a>Siehe auch

-   [Festlegen der Optionen des Ressourcen-Managers für Dateiserver](setting-file-server-resource-manager-options.md)


