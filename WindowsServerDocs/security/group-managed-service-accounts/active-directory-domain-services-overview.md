---
title: Übersicht über Active Directory Domain Services
description: Windows Server-Sicherheit
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.service: na
ms.suite: na
ms.technology: security-auditing
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6cfe9479-5d17-41d5-939a-891e5233fdca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: c0ee85358c5e39f1ebf8cd901298a6083a3ebb97
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403764"
---
# <a name="active-directory-domain-services-overview"></a>Übersicht über Active Directory Domain Services

>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016
  
Ein Verzeichnis ist eine hierarchische Struktur, in der Informationen zu Objekten im Netzwerk gespeichert werden. Ein Verzeichnisdienst, wie z. b. Active Directory Domain Services (AD DS), stellt die Methoden zum Speichern von Verzeichnis Daten und zum Bereitstellen dieser Daten für Netzwerk Benutzer und Administratoren bereit. AD DS speichert beispielsweise Informationen über Benutzerkonten, z. b. Namen, Kenn Wörter, Telefonnummern usw., und ermöglicht anderen autorisierten Benutzern im gleichen Netzwerk den Zugriff auf diese Informationen.  
  
Active Directory speichert Informationen zu Objekten im Netzwerk und erleichtert Administratoren und Benutzern das Auffinden und Verwenden dieser Informationen. Active Directory verwendet einen strukturierten Datenspeicher als Grundlage für eine logische, hierarchische Organisation der Verzeichnisinformationen.  
  
Dieser Datenspeicher, auch als Verzeichnis bezeichnet, enthält Informationen über Active Directory Objekte. Diese Objekte umfassen in der Regel freigegebene Ressourcen, z. b. Server, Volumes, Drucker und Netzwerk Benutzer-und Computer Konten. Weitere Informationen zum Active Directory Datenspeicher finden Sie unter [Verzeichnis Datenspeicher](https://technet.microsoft.com/library/cc736627(v=ws.10).aspx).  
  
Die Sicherheit wird in Active Directory durch die Anmelde Authentifizierung und die Zugriffs Steuerung für Objekte im Verzeichnis integriert. Bei einer einzelnen Netzwerk Anmeldung können Administratoren Verzeichnis Daten und die Organisation im gesamten Netzwerk verwalten, und autorisierte Netzwerk Benutzer können auf Ressourcen an beliebiger Stelle im Netzwerk zugreifen. Durch die richtlinienbasierte Verwaltung wird selbst die Verwaltung der komplexesten Netzwerke erleichtert. Weitere Informationen zur Active Directory Sicherheit finden Sie unter Sicherheitsübersicht.  
  
Active Directory umfasst auch Folgendes:  
* Ein Satz von Regeln, **das Schema**, das die Klassen von Objekten und Attributen definiert, die im Verzeichnis enthalten sind, die Einschränkungen und Begrenzungen für Instanzen dieser Objekte und das Format ihrer Namen. Weitere Informationen zum Schema finden Sie unter Schema.  
  
  
* Ein **globaler Katalog** , der Informationen zu jedem Objekt im Verzeichnis enthält. Dadurch können Benutzer und Administratoren Verzeichnisinformationen suchen, unabhängig davon, welche Domäne im Verzeichnis die Daten tatsächlich enthält. Weitere Informationen zum globalen Katalog finden Sie unter der Rolle des globalen Katalogs.  
  
  
* Ein **Abfrage-und Index Mechanismus**, sodass Objekte und ihre Eigenschaften veröffentlicht und von Netzwerk Benutzern oder-Anwendungen gefunden werden können. Weitere Informationen zum Abfragen des Verzeichnisses finden Sie untersuchen von Verzeichnisinformationen.  
  
  
* Ein **Replikations Dienst** , mit dem Verzeichnis Daten in einem Netzwerk verteilt werden. Alle Domänen Controller in einer Domäne nehmen an der Replikation Teil und enthalten eine vollständige Kopie aller Verzeichnisinformationen für Ihre Domäne. Jede Änderung an den Verzeichnisdaten wird zu allen Domänencontrollern in der Domäne repliziert. Weitere Informationen zur Active Directory Replikation finden Sie unter Übersicht über die Replikation.  
  
## <a name="understanding-active-directory"></a>Grundlegendes zu Active Directory  
 Dieser Abschnitt enthält Links zu den grundlegenden Active Directory Konzepten:  
   
* [Active Directory Struktur und Speichertechnologien](https://technet.microsoft.com/library/cc759186(v=ws.10).aspx)  
* [Domänen Controller Rollen](https://technet.microsoft.com/library/cc786438(v=ws.10).aspx)   
* Active Directory-Schema   
* [Understanding Trusts](https://technet.microsoft.com/library/cc771294(v=ws.10).aspx)   
* [Active Directory Replikations Technologien](https://technet.microsoft.com/library/cc786438(v=ws.10).aspx)   
* [Technologien für die Active Directory Suche und Veröffentlichung](https://technet.microsoft.com/library/cc775686(v=ws.10).aspx)   
* Interoperabilität mit DNS und Gruppenrichtlinie   
* [Grundlegendes zum Schema](https://technet.microsoft.com/library/cc759402(v=ws.10).aspx)   
  
Eine ausführliche Liste der Active Directory Konzepte finden Sie unter [Understanding Active Directory](https://technet.microsoft.com/library/cc781408(v=ws.10).aspx).   

