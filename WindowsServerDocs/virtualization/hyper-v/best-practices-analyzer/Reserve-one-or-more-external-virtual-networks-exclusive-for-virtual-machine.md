---
title: Reservieren Sie mindestens ein externes virtuelles Netzwerk für die ausschließliche Verwendung durch virtuelle Computer.
description: Enthält Anweisungen zum Beheben des Problems, das von dieser Best Practices Analyzer Regel gemeldet wird.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: f7732258-93f1-44e8-835b-5ad2d1c45cd9
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: a72f3d616bb0c520e49c27f90686196463f25953
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71364779"
---
# <a name="reserve-one-or-more-external-virtual-networks-for-exclusive-use-by-virtual-machines"></a>Reservieren Sie mindestens ein externes virtuelles Netzwerk für die ausschließliche Verwendung durch virtuelle Computer.

>Gilt für: Windows Server 2016

Weitere Informationen zu bewährten Methoden und Überprüfungen finden Sie unter [Best Practices Analyzer](https://go.microsoft.com/fwlink/?LinkId=122786).  
  
|Eigenschaft|Details|  
|-|-|  
|**Betriebssystem**|Windows Server 2016|  
|**Produkt/Feature**|Hyper-V|  
|**Zunehmen**|Fehler|  
|**Kategorie**|Konfiguration|  
  
In den folgenden Abschnitten gibt kursiv formatics den UI-Text an, der im Best Practices Analyzer Tool für dieses Problem angezeigt wird.  
  
## <a name="issue"></a>Problem  
  
*Alle externen virtuellen Netzwerke werden für die Verwendung durch das Verwaltungs Betriebssystem und die virtuellen Computer konfiguriert.*  
  
## <a name="impact"></a>Auswirkungen  
  
*Die Netzwerkleistung kann im Verwaltungs Betriebssystem beeinträchtigt werden.*  
  
## <a name="resolution"></a>Auflösung  
  
*Verwenden Sie Virtual Switch Manager, um die Freigabe eines externen virtuellen Netzwerks mit dem Verwaltungs Betriebssystem zu beenden.*  
  
#### <a name="to-stop-sharing-the-external-virtual-network-with-the-management-operating-system"></a>So verhindern Sie die Freigabe des externen virtuellen Netzwerks mit dem Verwaltungs Betriebssystem  
  
1.  Öffnen Sie den Hyper-V-Manager. Klicken Sie auf **Start**, zeigen Sie auf **Verwaltung**, und klicken Sie dann auf **Hyper-V-Manager**.  
  
2.  Klicken Sie im Menü **Aktionen** auf **Manager für virtuelle Switches**.  
  
3.  Klicken Sie unter **virtuelle Switches**auf den Namen des externen virtuellen Switches.  
  
4.  Deaktivieren Sie im Bereich **Verbindungstyp** unter dem Namen des physischen Netzwerkadapters das Kontrollkästchen **zulassen, dass das Verwaltungs Betriebssystem diesen Netzwerkadapter freigeben** kann.  
  
5.  Klicken Sie auf **OK**.  
  


