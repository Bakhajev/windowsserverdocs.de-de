---
title: Erweiterungen für Windows Admin Center
description: Erweiterungen für Windows Admin Center SDK (Projekt Honolulu)
ms.technology: extend
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 09/17/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: ee8c0203be25b30f173b1887de506844d5b58738
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71406911"
---
# <a name="extensions-for-windows-admin-center"></a>Erweiterungen für Windows Admin Center

>Gilt für: Windows Admin Center, Windows Admin Center-Vorschau

Windows Admin Center wird als eine erweiterbare Plattform zum Aktivieren von Partnern und Entwicklern und Funktionen in Windows Admin Center genutzt, integriert sich nahtlos in andere Produkte für IT-Administrationsprodukte und -Lösungen und mehr. Jede Lösung und jedes Tool im Windows Admin Center ist eine Erweiterung mit denselben Erweiterungsfeatures für Partner und Entwickler, damit Sie die in Windows Admin Center verfügbaren leistungsstarken Tools nutzen können.

Windows Admin Center-Erweiterungen basieren auf modernen Webtechnologien einschließlich HTML5, CSS, Angular, TypeScript and jQuery und verwalten Zielserver über PowerShell oder WMI. Sie können auch Zielserver, Dienste oder Geräte über unterschiedliche Protokolle wie REST verwalten, durch die Erstellung eines Windows Admin Center Gateway-Plug-In.

## <a name="why-you-should-consider-developing-an-extension-for-windows-admin-center"></a>Warum Sie die Entwicklung einer Erweiterung für das Windows Admin Center in Betracht ziehen sollten

Hier ist der Wert, den Sie für Ihr Produkt und ihre Kunden nutzen können, indem Sie Erweiterungen für Windows Admin Center entwickeln:

- **Integration in Windows Admin Center-Tools:** Integrieren Sie Ihre Produkte und Dienste in die Server-und Cluster Verwaltungs Tools in Windows Admin Center, und stellen Sie Ihren Kunden eine einheitliche, nahtlose End-to-End-Überwachung, Verwaltung und Problembehandlung bereit.
- **Nutzen Sie Plattformsicherheit, Identitäts-und Verwaltungsfunktionen:** Aktivieren Sie die Unterstützung von Azure Active Directory (AAD), Multi-Factor Authentication, rollenbasierten Access Control (Role-Based, RBAC), Protokollierung, Überwachung für Ihr Produkt und ihre Dienste, indem Sie die Funktionen der Windows Admin Center-Plattform nutzen, um die komplexen Anforderungen IT-Organisationen.
- **Entwickeln Sie mit den neuesten Webtechnologien:** Erstellen Sie mit modernen Webtechnologien, wie z.b. HTML5, CSS, Angular, typescript und jQuery, und umfangreiche, leistungsstarke UI-Steuerelemente, die im Windows Admin Center SDK enthalten sind, schnell beeindruckende Benutzererfahrung.
- **Erweitern der Produktbetreuung:** Nehmen Sie an der neuen Windows Admin Center-Umgebung Teil, und profitieren Sie von unserer schnell wachsenden Kundenbasis und nutzen die Windows Server 2019-Start Dynamik später in diesem Jahr.

## <a name="start-developing-with-the-windows-admin-center-sdk"></a>Beginnen Sie mit der Entwicklung mit dem Windows Admin Center SDK

Der Einstieg in die Entwicklung des Windows Admin Centers ist einfach!  Den Beispielcode finden Sie in unserer SDK-Dokumentation für [Tool](develop-tool.md) [-, Projektmappen-und](develop-solution.md)Gateway- [Plug](develop-gateway-plugin.md) -in-Erweiterungs Typen. Dort verwenden Sie die Windows Admin Center-CLI, um ein neues Erweiterungsprojekt zu erstellen, und befolgen dann die einzelnen Leitfäden, um Ihr Projekt an Ihre Anforderungen anzupassen.

Wir haben ein Windows Admin Center [SDK-Entwurfs-Toolkit](https://github.com/Microsoft/windows-admin-center-sdk/blob/master/WindowsAdminCenterDesignToolkit.zip) zur Verfügung gestellt, mit dem Sie Erweiterungen in PowerPoint mithilfe von Windows Admin Center-Stilen,-Steuerelementen und-Seitenvorlagen schnell bereinigen können. Sehen Sie sich an, wie Ihre Erweiterung im Windows Admin Center aussehen kann, bevor Sie mit dem Programmieren beginnen!

Außerdem haben wir Beispielcode auf GitHub gehostet: [Entwicklertools](https://aka.ms/wacsdk) ist eine Beispiel-projektmappenerweiterung mit einer umfangreichen Sammlung von Steuerelementen, die Sie durchsuchen und in ihrer eigenen Erweiterung verwenden können. Entwicklertools ist eine voll funktionsfähige Erweiterung, die in Windows Admin Center im Entwicklermodus Seite geladen werden können.

Lesen Sie die Themen unten, um mehr über das SDK und die ersten Schritte zu erfahren:

- [Verstehen der Funktionsweise von Erweiterungen](understand-extensions.md)
- [Entwickeln einer Erweiterung](developing-extensions.md)
- [Handbücher](guides.md)
- [Veröffentlichen der Erweiterung](publish-extensions.md)

## <a name="partner-spotlight"></a>Partner Spotlight

Sehen Sie den Wert, den unsere Partner mit dem Windows Admin Center-Ökosystem haben und probieren Sie die Erweiterungen heute aus. Auf [Erweiterungen installieren](../configure/using-extensions.md) im Windows Admin Center erfahren Sie mehr.

### <a name="biitops"></a>Biitops
Die Erweiterung für biitops-Änderungen bietet Änderungs Nachverfolgung für Hardware-, Software-und Konfigurationseinstellungen auf ihren physischen/virtuellen Windows Server-Computern. Die Erweiterung für biitops-Änderungen zeigt genau, was neu ist, was sich geändert hat und was in einem einzelnen Bereich gelöscht wurde, um Probleme im Zusammenhang mit Compliance, Zuverlässigkeit und Sicherheit zu verfolgen. [Erfahren Sie mehr über die Erweiterung für biitops-Änderungen](case-studies/biitops.md).

![Biitops-Erweiterung](../media/extensibility-overview/biitops-1.png)

### <a name="dataon"></a>DataON

Die Erweiterung "DataOn" muss über die Erweiterung "Überwachung", "Verwaltung" und "End-to-End" in der hyperkonvergierten Infrastruktur und in den Speichersystemen von Daten auf Basis von Windows Server. Die Erweiterung muss einen eindeutigen Wert hinzufügen, wie z. b. Verlaufs Daten Berichte, Datenträger Zuordnung, Systemwarnungen und San-ähnlichen CallHome Service, ergänzt den Windows Admin Center-Server und die hyperkonvergenten Infrastruktur Verwaltungsfunktionen durch nahtlose, einheitliche Funktionen. [Erfahren Sie mehr über DataON's MUST-Erweiterungen und die Erfahrung der Entwicklung](case-studies/dataon.md).

![DataON MUST-Erweiterung](../media/extensibility-overview/dataon-must-extension.png)

### <a name="fujitsu"></a>Fujitsu

Die ServerView Health-und RAID-Integritäts Erweiterungen von Fujitsu für Windows Admin Center bieten eine ausführliche Überwachung und Verwaltung kritischer Hardwarekomponenten wie z. b. Prozessoren, Arbeitsspeicher, Energie-und Speicher Subsysteme für Fujitsu PRIMERGY-Server. Durch das Windows Admin Center UX Entwurfsmuster und UI-Steuerelemente, hat Fujitsu einen großen Schritt zur unsere Vision der End-to-End-Einblick in die Serverrollen und Dienste, Betriebssysteme sowie die Verwaltung von Hardware über die Windows Admin Center Geschäftswelt Plattform gemacht. [Erfahren Sie mehr über Fujitsu-Erweiterungen und die Erfahrung in der Entwicklung](case-studies/fujitsu.md).

![Fujitsu ServerView-Erweiterung](../media/extensibility-overview/fujitsu-serverview-extension.png)

### <a name="lenovo"></a>Lenovo

Die Lenovo xclarity Integrator-Erweiterung übernimmt die Hardware Verwaltung auf der nächsten Ebene, indem Sie nahtlos in verschiedene Umgebungen in Windows Admin Center integriert wird. Die xclarity Integrator-Lösung bietet eine allgemeine Übersicht über alle Lenovo-Server, und verschiedene Tool Erweiterungen stellen Hardware Details bereit, unabhängig davon, ob Sie mit einem einzelnen Server, einem Failovercluster oder einem hyperkonvergenten Cluster verbunden sind. [Erfahren Sie mehr über die Lenovo xclarity Integrator-Erweiterung](case-studies/lenovo.md).

![Lenovo-Erweiterung](../media/extensibility-overview/lenovo-extension.png)

### <a name="pure-storage"></a>Pure Storage

Reiner Speicher bietet Enterprise-, all-Flash-Datenspeicherlösungen, die datenzentrierte Architekturen bereitstellen, um Ihr Unternehmen auf einen Wettbewerbsvorteil zu beschleunigen. Die reine Speichererweiterung für das Windows Admin Center bietet eine Ansicht im einzelnen Bereich für reine flasharray-Produkte und ermöglicht Benutzern das Durchführen von Überwachungsaufgaben, das Anzeigen von Echt Zeit Leistungsmetriken und das Verwalten von Speichervolumes und Initiatoren über eine einzige Benutzeroberfläche. Erlebnis. [Erfahren Sie mehr über die reinen Erweiterungen und deren Entwicklungs](case-studies/purestorage.md)Möglichkeiten.

![Reine Speichererweiterung](../media/extensibility-overview/purestorage-extension.png)

### <a name="qct"></a>QCT

Die qct Management Suite-Erweiterung ergänzt Windows Admin Center durch die Bereitstellung physischer Serverüberwachung und-Verwaltung für qct-Azure Stack HCI-zertifizierte Systeme. Die qct Management Suite-Erweiterung zeigt Server Hardwareinformationen an und bietet eine intuitive Assistent-Benutzeroberfläche, die Ihnen hilft, physische Datenträger effizient zu ersetzen, Hardware-Ereignisprotokoll Tools und S.M.A.R.T. basierte Verwaltung vorhersag barer Datenträger. [Erfahren Sie mehr über die qct Management Suite-Erweiterung](case-studies/qct.md).

![Qct-Erweiterung](../media/extensibility-overview/qct-extension.png)

### <a name="squared-up"></a>Squared Up

Squared Up bietet eine optimale Erfahrung basierend auf System Center Operations Manager und integriert Azure Log Analytics, Application Insights und anderen Monitoring-Lösungen. Die [Erweiterung Squared Up](https://squaredup.com/product/honolulu/windows-admin-center-extension/?utm_source=microsoft-docs&utm_medium=public-relations&utm_campaign=honolulu) ermöglicht optimale Leistungsdaten und Live-Anwendungstopologien und Abhängigkeiten im Kontext von Server- und Clusterverwaltung des Windows Admin Centers. Vorherige Kunden sehen den Wert der immensen Datenzufuhr aus vielen unterschiedlichen Quellen in eine einzelne Quelle. [Erfahren Sie mehr über Squared Up und die Erfahrung in der Entwicklung](case-studies/squared-up.md).

![Squared Up-Erweiterung](../media/extensibility-overview/squaredup-extension.png)