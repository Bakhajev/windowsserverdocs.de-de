---
title: Verwalten von Remotespeicherressourcen
description: "In diesem Artikel wird beschrieben, wie Sie Speicherressourcen einem Remotecomputer verwalten können."
ms.date: 7/7/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 583c36f399848cf67c6f3a850e62015b224768d9
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2017
---
# <a name="managing-remote-storage-resources"></a>Verwalten von Remotespeicherressourcen

> Gilt für: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Wenn Sie Speicherressourcen auf einem Remotecomputer verwalten möchten, haben Sie zwei Optionen:

-   Verbinden Sie vom MMC-Snap-In (Microsoft Management Console) des Ressourcen-Managers für Dateiserver<sup>®</sup> aus den Remotecomputer (das Sie anschließend zum Verwalten der Remote-Ressourcen verwenden können).
-   Verwenden Sie die Befehlszeilentools, die auf dem Ressourcen-Manager für Dateiserver installiert sind.

Beide Optionen ermöglichen Ihnen, Kontingente zu verwalten, Dateien zu überprüfen, Klassifizierungen zu verwalten, Dateiverwaltungsaufgaben zu planen und Berichte mit diesen Remote-Ressourcen zu verwalten.

> [!Note]
> Der Ressourcen-Manager für Dateiserver kann Ressourcen auf dem lokalen Computer oder auf einem Remotecomputer verwalten, jedoch nicht gleichzeitig.

Sie haben u. a. folgende Möglichkeiten:

-   Stellen Sie mithilfe des MMC-Snap-In (Microsoft Management Console) des Ressourcen-Managers für Dateiserver eine Verbindung mit einem anderen Computer in der Domäne her und überprüfen Sie die Speichernutzung eines Volume oder eines Ordners auf dem Remotecomputer.
-   Erstellen Sie Kontingent- und Datenprüfungsvorlagen auf einem lokalen Server und verwenden Sie anschließend die Befehlszeilentools, um diese Vorlagen in einem Dateiserver in einer Zweigstelle zu importieren.

In diesem Abschnitt werden folgende Themen behandelt:

-   [Verbindung mit einem Remotecomputer herstellen](connect-to-remote-computer.md)
-   [Befehlszeilentools](command-line-tools.md)