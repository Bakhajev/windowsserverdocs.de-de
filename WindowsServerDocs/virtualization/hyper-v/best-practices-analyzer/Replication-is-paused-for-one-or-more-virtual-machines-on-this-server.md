---
title: Die Replikation für mindestens eine virtuelle Maschine auf diesem Server wurde angehalten.
description: Online Version des Texts für diese Best Practices Analyzer Regel.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: e1119a40-eda3-4058-8648-7df81cbc6c29
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 17d50f116c6cee488367c924bfbce3791a8d879f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393539"
---
# <a name="replication-is-paused-for-one-or-more-virtual-machines-on-this-server"></a>Die Replikation für mindestens eine virtuelle Maschine auf diesem Server wurde angehalten.

>Gilt für: Windows Server 2016

Weitere Informationen zu bewährten Methoden und Scans finden Sie unter [Ausführen von Best Practices Analyzer Scans und Verwalten der Scan Ergebnisse](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Eigenschaft|Details|  
|-|-|  
|**Betriebssystem**|Windows Server 2016|  
|**Produkt/Feature**|Hyper-V|  
|**Zunehmen**|Warnung|  
|**Kategorie**|Vorgänge|  
  
In den folgenden Abschnitten gibt kursiv formatics den UI-Text an, der im Best Practices Analyzer Tool für dieses Problem angezeigt wird.  
  
## <a name="issue"></a>Problem  
die *replikation wurde für mindestens einen virtuellen Computer angehalten. Während der primäre virtuelle Computer angehalten wird, werden alle auftretenden Änderungen akkumuliert und nach dem Fortsetzen der Replikation an den virtuellen Replikat Computer gesendet.*  
  
## <a name="impact"></a>Auswirkungen  
*solange die Replikation angehalten ist, verbraucht akkumulierte Änderungen, die auf dem primären virtuellen Computer auftreten, den verfügbaren Speicherplatz auf dem primären Server. Nach dem Fortsetzen der Replikation kann es zu einem großen Anstieg des Netzwerk Datenverkehrs zum Replikat Server kommen. Dies wirkt sich auf die folgenden virtuellen Computer aus:*  
  
\<list of Virtual Machines >  
  
## <a name="resolution"></a>Auflösung  
*vergewissern Sie sich, dass das Anhalten der Replikation beabsichtigt war. Wenn die Replikation angehalten wurde, um wenig Speicherplatz oder Netzwerk Konnektivität zu beheben, setzen Sie die Replikation fort, sobald diese Probleme behoben sind.*  
  


