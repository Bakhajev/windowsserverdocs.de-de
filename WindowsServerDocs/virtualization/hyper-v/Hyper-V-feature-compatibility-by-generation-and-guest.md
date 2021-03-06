---
title: Kompatibilität von Hyper-V-Features nach Generierung und Gast
description: Listet die Generationen und Betriebssysteme auf, die mit den wichtigsten Hyper-V-Features kompatibel sind.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 81c1f32d-7814-4992-8a66-dd4b77c939b4
author: KBDAzure
ms.author: kathydav
ms.date: 12/05/2016
ms.openlocfilehash: cdca6c31ff14fe63e99ec4afa2581885677bb61d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71365538"
---
# <a name="hyper-v-feature-compatibility-by-generation-and-guest"></a>Kompatibilität von Hyper-V-Features nach Generierung und Gast

>Gilt für: Windows Server 2016
  
Die Tabellen in diesem Artikel veranschaulichen die Generationen und Betriebssysteme, die mit einigen der Hyper-V-Features kompatibel sind und nach Kategorien gruppiert sind. Im Allgemeinen erhalten Sie die beste Verfügbarkeit von Features mit einem virtuellen Computer der Generation 2, auf dem das neueste Betriebssystem ausgeführt wird.  
  
Beachten Sie, dass einige Features von Hardware oder anderen Infrastrukturen abhängen. Hardware Details finden Sie unter [System Anforderungen für Hyper-V auf Windows Server 2016](System-requirements-for-Hyper-V-on-Windows.md). In einigen Fällen kann ein Feature mit allen unterstützten Gastbetriebssystemen verwendet werden. Ausführliche Informationen dazu, welche Betriebssysteme unterstützt werden, finden Sie unter:  
  
* [Unterstützte virtuelle Linux-und FreeBSD-Computer](Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows.md)  
* [Unterstützte Windows-Gastbetriebssysteme](Supported-Windows-guest-operating-systems-for-Hyper-V-on-Windows.md)  
  
## <a name="availability-and-backup"></a>Verfügbarkeit und Sicherung  
  
Feature  | Stro | Gastbetriebssystem  
------------- | ------------- | -----------  
Prüfpunkte | 1 und 2 | Jeder unterstützte Gast  
Gastclustering | 1 und 2 | Gäste, die Cluster fähige Anwendungen ausführen und die iSCSI-Ziel Software installiert haben  
Replikation | 1 und 2 | Jeder unterstützte Gast  
Domänencontroller | 1 und 2 | Alle unterstützten Windows Server-Gäste, die nur Produktions Prüfpunkte verwenden. Siehe [unterstützte Windows Server-Gast Betriebssysteme](https://docs.microsoft.com/windows-server/virtualization/hyper-v/supported-windows-guest-operating-systems-for-hyper-v-on-windows#supported-windows-server-guest-operating-systems)   
  
## <a name="compute"></a>Compute  
  
Feature  | Stro | Gastbetriebssystem  
------------- | ------------- | -----------  
Dynamischer Arbeitsspeicher | 1 und 2 | Bestimmte Versionen von unterstützten Gästen. Weitere Informationen finden Sie unter [Übersicht über Hyper-V-dynamischer Arbeitsspeicher](https://technet.microsoft.com/library/hh831766.aspx) für ältere Versionen als Windows Server 2016 und Windows 10.  
Heißes hinzufügen/entfernen des Speichers | 1 und 2 | Windows Server 2016, Windows 10  
Virtuelle NUMA | 1 und 2 | Jeder unterstützte Gast  
  
## <a name="development-and-test"></a>Entwicklung und Test  
Feature  | Stro | Gastbetriebssystem  
------------- | ------------- | -----------  
COM/serielle Anschlüsse | 1 und 2 <br>**Hinweis**: Verwenden Sie für Generation 2 Windows PowerShell, um zu konfigurieren. Weitere Informationen finden [Sie unter Hinzufügen eines COM-Ports für das Kernel Debugging](./plan/should-i-create-a-generation-1-or-2-virtual-machine-in-hyper-v.md#add-a-com-port-for-kernel-debugging). | Jeder unterstützte Gast  
  
## <a name="mobility"></a>Mobilität  
  
Feature  | Stro | Gastbetriebssystem  
------------- | ------------- | -----------  
Livemigration  | 1 und 2 |  Jeder unterstützte Gast  
Importieren/Exportieren | 1 und 2 |  Jeder unterstützte Gast  
  
## <a name="networking"></a>Netzwerk  
  
Feature  | Stro | Gastbetriebssystem  
------------- | ------------- | -----------  
Heißes hinzufügen/entfernen des virtuellen Netzwerkadapters | 2 | Jeder unterstützte Gast  
Virtueller Legacy-Netzwerkadapter | 1 | Jeder unterstützte Gast  
Single root Input/Output Virtualization (SR-IOV) | 1 und 2 | 64-Bit-Windows-Gast Betriebssysteme, beginnend mit Windows Server 2012 und Windows 8.  
Multiqueue für virtuelle Computer (vmmq) | 1 und 2  | Jeder unterstützte Gast  
  
## <a name="remote-connection-experience"></a>Remote Verbindung  
  
Feature  | Stro | Gastbetriebssystem  
------------- | ------------- | -----------  
Diskrete Geräte Zuweisung (DDA) | 1 und 2 | Windows Server 2016, Windows Server 2012 R2 nur mit installiertem Update 3133690, Windows 10 <br> **Hinweis**: Ausführliche Informationen zu Update 3133690 finden Sie in [diesem](https://support.microsoft.com/kb/3133690) Support Artikel.  
Verbesserter Sitzungsmodus | 1 und 2 | Windows Server 2016, Windows Server 2012 R2, Windows 10 und Windows 8.1 mit aktiviertem Remotedesktopdienste <br>**Hinweis**: Möglicherweise müssen Sie auch den Host konfigurieren. Weitere Informationen finden Sie unter [Verwenden lokaler Ressourcen auf einem virtuellen Hyper-V-Computer mit VMConnect](./learn-more/Use-local-resources-on-Hyper-V-virtual-machine-with-VMConnect.md).  
RemoteFx | 1 und 2 | Generation 1 auf 32-und 64-Bit-Windows-Versionen ab Windows 8. <br> Generation 2 auf 64-Bit-Windows 10-Versionen  
  
## <a name="security"></a>Sicherheit  
  
Feature  | Stro | Gastbetriebssystem  
------------- | ------------- | -----------  
Sicherer Start | 2 | **Linux**: Ubuntu 14,04 und höher, SuSE Linux Enterprise Server 12 und höher, Red Hat Enterprise Linux 7,0 und höher und CentOS 7,0 und höher<br>**Windows**: Alle unterstützten Versionen, die auf einem virtuellen Computer der Generation 2 ausgeführt werden können  
Abgeschirmte VMs | 2 | **Windows**: Alle unterstützten Versionen, die auf einem virtuellen Computer der Generation 2 ausgeführt werden können  
  
## <a name="storage"></a>Speicher  
  
Feature  | Stro | Gastbetriebssystem  
------------- | ------------- | -----------  
Freigegebene virtuelle Festplatten (nur vhdx) | 1 und 2  | Windows Server 2016, Windows Server 2012 R2, Windows Server 2012  
SMB3 | 1 und 2 | Alle, die SMB3 unterstützen  
Direkte Speicherplätze | 2 | Windows Server 2016  
Virtueller Fibre Channel | 1 und 2 | Windows Server 2016, Windows Server 2012 R2, Windows Server 2012  
Vhdx-Format | 1 und 2 | Jeder unterstützte Gast   
  
  
  
  
    


