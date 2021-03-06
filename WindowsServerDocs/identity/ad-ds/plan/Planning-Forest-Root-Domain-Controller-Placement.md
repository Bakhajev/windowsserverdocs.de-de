---
ms.assetid: 2a2f493a-9796-454a-9721-e223b799dfa7
title: Planen der Platzierung der Stammdomänencontroller der Gesamtstruktur
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: e619d5f5e9cc317f9ba1548d5ed3a32e7bd12c2c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402548"
---
# <a name="planning-forest-root-domain-controller-placement"></a>Planen der Platzierung der Stammdomänencontroller der Gesamtstruktur

>Gilt für: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Zum Erstellen von Vertrauens Pfaden für Clients, die auf Ressourcen in anderen Domänen als ihren eigenen zugreifen müssen, sind Gesamtstruktur-Stamm Domänen Controller erforderlich. Platzieren Sie Gesamtstruktur-Stamm Domänen Controller an Hub-Standorten und an Standorten, die Daten Center hosten Wenn Benutzer an einem bestimmten Speicherort auf Ressourcen aus anderen Domänen am gleichen Speicherort zugreifen müssen und die Netzwerkverfügbarkeit zwischen dem Rechenzentrum und dem Speicherort des Benutzers unzuverlässig ist, können Sie entweder einen Gesamtstruktur-Stamm Domänen Controller am Standort hinzufügen oder einen Vertrauensstellung zwischen den beiden Domänen. Es ist kostengünstiger, eine Vertrauensstellung zwischen den Domänen zu erstellen, es sei denn, Sie haben andere Gründe, einen Gesamtstruktur-Stamm Domänen Controller an diesem Speicherort zu platzieren.  
  
Vertrauens Stellungen helfen bei der Optimierung von Authentifizierungsanforderungen von Benutzern, die sich in einer der beiden Domänen befinden. Weitere Informationen zu Verknüpfungs Vertrauensstellungen zwischen Domänen finden Sie im Artikel grundlegendes [zum Erstellen einer Vertrauensstellungs Abkürzung](https://go.microsoft.com/fwlink/?LinkId=107061).  
  
Ein Arbeitsblatt, das Sie bei der Dokumentation der Stamm Domänen Controller-Platzierung Ihres Gesamtstruktur-Stamm Verzeichnisses unterstützt, finden Sie unter [Job Aids for Windows Server 2003 Deployment Kit](https://go.microsoft.com/fwlink/?LinkID=102558), Download Job_Aids_Designing_and_Deploying_Directory_and_Security_Services. zip und Open "Domain Controller Platzierung "(DSSTOPO_4. doc).  
  
Sie müssen diese Informationen beachten, wenn Sie die Stamm Domäne der Gesamtstruktur erstellen. Weitere Informationen zum Bereitstellen der Stamm Domäne der Gesamtstruktur finden Sie unter Bereitstellen [einer Windows Server 2008](https://technet.microsoft.com/library/cc731174.aspx)-Gesamtstruktur-Stamm Domäne.  
