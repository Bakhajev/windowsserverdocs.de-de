---
title: Konfigurieren Sie mindestens die erforderliche Arbeitsspeicher Menge für einen virtuellen Computer, auf dem Windows Server 2012 R2 ausgeführt wird und für den dynamischer Arbeitsspeicher aktiviert ist.
description: Online Version des Texts für diese Best Practices Analyzer Regel.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: a0e69661-6a1d-4b31-b727-f2429f3977d0
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: 5d770c43f18852896aacff0922875855f01e9711
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71364994"
---
# <a name="configure-at-least-the-required-amount-of-memory-for-a-virtual-machine-running-windows-server-2012-r2-and-enabled-for-dynamic-memory"></a>Konfigurieren Sie mindestens die erforderliche Arbeitsspeicher Menge für einen virtuellen Computer, auf dem Windows Server 2012 R2 ausgeführt wird und für den dynamischer Arbeitsspeicher aktiviert ist.

>Gilt für: Windows Server 2016

Weitere Informationen zu bewährten Methoden und Scans finden Sie unter [Ausführen von Best Practices Analyzer Scans und Verwalten der Scan Ergebnisse](https://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|Eigenschaft|Details|  
|-|-|  
|**Betriebssystem**|Windows Server 2016|  
|**Produkt/Feature**|Hyper-V|  
|**Zunehmen**|Fehler|  
|**Kategorie**|Konfiguration|  
  
In den folgenden Abschnitten gibt kursiv formatics den UI-Text an, der im Best Practices Analyzer Tool für dieses Problem angezeigt wird.  
  
## <a name="issue"></a>**Problem:**  
*Mindestens ein virtueller Computer ist für die Verwendung von dynamischer Arbeitsspeicher mit weniger als dem für Windows Server 2012 R2 erforderlichen Arbeitsspeicher konfiguriert.*  
  
## <a name="impact"></a>**Auswirkt**  
*Das Gast Betriebssystem auf den folgenden virtuellen Computern wird möglicherweise nicht ausgeführt oder kann nicht zuverlässig ausgeführt werden:*  
  
\<list of Virtual Machines >  
  
## <a name="resolution"></a>**Auflösung**  
*Verwenden Sie den Hyper-V-Manager, um den minimalen Arbeitsspeicher auf mindestens 256 MB und den Start Speicher und den maximalen Arbeitsspeicher für diesen virtuellen Computer auf mindestens 512 MB zu erhöhen.*  
  
### <a name="increase-memory-using-hyper-v-manager"></a>Erhöhen des Arbeitsspeichers mit dem Hyper-V-Manager  
  
1.  Öffnen Sie den Hyper-V-Manager. ( **Klicken Sie**in Server-Manager auf Extras  > **Hyper-V-Manager**.)  
  
2.  Klicken Sie in der Liste der virtuellen Computer mit der rechten Maustaste auf das gewünschte, und klicken Sie dann auf **Einstellungen**.  
  
3.  Klicken Sie im Navigationsbereich auf Arbeits **Speicher**.  
  
4.  Ändern Sie den **RAM** auf mindestens 512 MB.  
  
5.  Ändern Sie unter **dynamischer Arbeitsspeicher**den **minimalen RAM** auf mindestens 256 MB und den **maximalen RAM** auf 512 MB.  
  
6.  Klicken Sie auf **OK**.  
  
### <a name="increase-memory-using-windows-powershell"></a>Erhöhen des Arbeitsspeichers mithilfe von Windows PowerShell  
  
1.  Öffnen Sie Windows PowerShell. (Klicken Sie auf dem Desktop auf **Start** , und beginnen Sie mit der Eingabe von **Windows PowerShell**.)  
  
2.  Klicken Sie mit der rechten Maustaste auf **Windows PowerShell** und dann auf **als Administrator ausführen**.  
  
3.  Führen Sie einen Befehl aus, der dem folgenden ähnelt, und ersetzen Sie dabei MyVM durch den Namen des virtuellen Computers und die Arbeitsspeicher Werte mit mindestens den unten gezeigten Werten.  
  
```  
Get-VM MyVM | Set-VMMemory -DynamicMemoryEnabled $True -MaximumBytes 512MB -MinimumBytes 256MB -StartupBytes 512MB  
```  
  


