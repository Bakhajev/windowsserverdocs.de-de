---
title: Assistent für die Serverbereinigung
description: 'Thema zu Windows Server Update Service (WSUS): Verwenden des Assistenten zum Bereinigen von Servern zum Verwalten von Speicherplatz'
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-wsus
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c351797-2716-4442-a668-60d5b4e77751
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e285e59a27b6bf0ef1bf3b1ab0f78a96efa60c87
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71361533"
---
# <a name="the-server-cleanup-wizard"></a>Assistent für die Serverbereinigung

>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Der Server Bereinigung-Assistent ist in die Benutzeroberfläche integriert und kann verwendet werden, um Ihnen bei der Verwaltung des Speicherplatzes zu helfen. Mit diesem Assistenten können die folgenden Vorgänge ausgeführt werden:

- Entfernen nicht verwendeter Updates und Update Revisionen entfernen Sie alle älteren Updates, und aktualisieren Sie Revisionen, die nicht genehmigt wurden.

- Löschen Sie Computer, die keine Verbindung mit dem Server herstellen, löschen Sie alle Client Computer, die den Server innerhalb von dreißig Tagen oder mehr nicht kontaktiert haben

- Nicht benötigte Update Dateien löschen löscht alle Update Dateien, die nicht von Updates oder Downstreamservern benötigt werden.

- Abgelaufene Updates ablehnen ablehnen alle Updates, die von Microsoft abgelaufen sind.

- Ablehnen von abgelösten Updates ablehnen alle Updates, die alle folgenden Kriterien erfüllen:

  -   Das ersetzte Update ist nicht obligatorisch.

  -   Das erersetzte Update befindet sich seit dreißig Tagen oder länger auf dem Server.

  -   Das erersetzte Update wird zurzeit von keinem Client als erforderlich gemeldet.

  -   Das abgelösten Update wurde mindestens 90 Tage lang nicht explizit für eine Computergruppe bereitgestellt.

  -   Das ersetzende Update muss für die Installation in einer Computergruppe genehmigt werden.

  > [!WARNING]
  >  In einer WSUS-Hierarchie wird dringend empfohlen, zuerst den Bereinigungs Prozess auf dem untersten, Downstream/Replikat-WSUS-Server auszuführen und dann die Hierarchie nach oben zu verschieben. Eine nicht ordnungsgemäße Ausführung der Bereinigung auf einem Upstream-Server vor dem Ausführen der Bereinigung auf jedem Downstreamserver kann zu einem Konflikt zwischen den Daten in upstreamdatenbanken und downstreamdatenbanken führen. Der Daten Konflikt kann zu Synchronisierungs Fehlern zwischen den Upstream-und Downstreamservern führen. 
  > 
  > [!IMPORTANT]
  >  Wenn Sie unnötige Inhalte mit dem Server Bereinigungs-Assistenten entfernen, werden alle privaten Update Dateien, die Sie von der Microsoft Update Katalog-Website heruntergeladen haben, ebenfalls entfernt. Sie müssen diese Dateien nach dem Ausführen des Server Bereinigungs-Assistenten erneut importieren. 

Wenn Updates mithilfe einer Regel für die automatische Genehmigung genehmigt werden, befinden Sie sich möglicherweise weiterhin im Status "genehmigt" und werden nicht durch den Server Bereinigungs-Assistenten entfernt. Zum Entfernen automatisch genehmigter Updates, die den Status "genehmigt" aufweisen, muss der WSUS-Administrator mindestens manuell den Genehmigungs Status der abgelösten Updates auf "nicht genehmigt" festlegen, damit Sie vom Server Bereinigungs-Assistenten zur Entschlüsselung berechtigt werden. Der Server Bereinigung-Assistent stellt sicher, dass ein neueres Update genehmigt wird und dass das Update von keinem Client System nach Bedarf gemeldet wird, bevor das Update als "abgelehnt" markiert wird.




