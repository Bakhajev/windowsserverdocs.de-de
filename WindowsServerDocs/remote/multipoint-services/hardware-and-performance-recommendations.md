---
title: Hardwareanforderungen und Empfehlungen zur Leistung
description: Bietet Hardware-und Leistungsanforderungen sowie Empfehlungen für Multipoint Services
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99a5c9c2-270f-4753-a28c-434882c03125
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: 284131028b308ee86389f25102d934390ba2f16d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71389110"
---
# <a name="hardware-requirements-and-performance-recommendations"></a>Hardwareanforderungen und Empfehlungen zur Leistung
In diesem Thema wird die Hardware beschrieben, die zum Ausführen eines Multipoint Services-Systems und zum unterstützen von Anwendungsszenarien für Benutzer erforderlich ist. Das Benutzer Szenario wirkt sich direkt auf die CPU-, RAM-und Netzwerk Bandbreitenanforderungen aus.  

## <a name="optimize-multipoint-services-system-performance"></a>Optimieren der Multipoint Services-Systemleistung  
Die Leistung des Multipoint Services-Systems wird direkt von der Kapazität der CPU, der GPU und der RAM-Kapazität, die auf dem Computer verfügbar ist, auf dem Multipoint Services ausgeführt wird, beeinträchtigt.  
  
### <a name="applications-and-internet-content"></a>Anwendungen und Internet Inhalte  
Da Multipoint Services eine Lösung für die gemeinsame Nutzung von Ressourcen ist, können sich der Typ und die Anzahl der Anwendungen, die auf den Stationen ausgeführt werden, auf die Leistung Ihres Multipoint Services-Systems auswirken. Es ist wichtig, die Typen von Programmen zu beachten, die bei der Planung Ihres Systems regelmäßig verwendet werden. Beispielsweise erfordert eine grafikintensive Anwendung einen leistungsfähigeren Computer als eine Anwendung, z. b. ein Textverarbeitungs Tool. Das über Laden des Computers mit Grafik intensiven Anwendungen führt wahrscheinlich zu Verzögerungen beim gesamten System.  
  
Der Inhaltstyp, auf den Anwendungen zugreifen, wirkt sich auch auf die Leistung des Systems aus. Wenn mehrere Stationen Webbrowser für den Zugriff auf Multimedia-Inhalte verwenden, wie z. b. vollbewegungs-Video, können vor der Beeinträchtigung der Systemleistung weniger Stationen verbunden werden. Wenn dagegen mehrere Stationen Webbrowser verwenden, um auf statische Webinhalte zuzugreifen, können mehr Stationen ohne erhebliche Auswirkung auf die Leistung verbunden werden.  
  
### <a name="hardware-recommendations"></a>Hardware-Empfehlungen  
Verwenden Sie die Richtlinien in der folgenden Tabelle, wenn Sie Ihr System planen und testen, um eine gute Leistung mit Ihrem Multipoint Services-System zu erzielen. Dies sind die grundlegenden Anforderungen für die Multipoint-Dienste. Die tatsächliche Konfigurations Größe hängt von Ihrer Systemkonfiguration, der Arbeitsauslastung, die Sie ausführen, und der Hardware Funktion ab. Sie sollten stets validieren, indem Sie Ihre Anwendungen und Hardware testen.  
  
> [!NOTE]  
> 2C = 2 Kerne, 4C = 4 Kerne, 6C = 6 Kerne, MT = Multithreading. Die Prozessorgeschwindigkeit muss mindestens 2,0 Gigahertz (GHz) betragen.  
  
### <a name="minimum-recommended-hardware-for-running-default-multipoint-server-stations"></a>Empfohlene Hardware für die Ausführung von Standard-Multipoint-Server Stationen  
  
|Anwendungsszenario|Bis zu 5 Stationen|6-8-Stationen|9-12-Stationen|13-16-Stationen|17-20-Stationen|21-24-Stationen|  
|------------------------|----------------------|-------------------|------------------|-------------------|-------------------|-----------------|  
|**Fak**<br /><br />Office, Webbrowser, Branchen Anwendungen|CPU: 2C<br /><br />RAM: 2 GB|CPU: 2C<br /><br />RAM: 4 GB|CPU: 4C<br /><br />RAM: 6 GB|CPU: 4C<br /><br />RAM: 8 GB|CPU: 4C + MT oder 6C<br /><br />RAM: 10 GB| CPU: 6C + MT<br /><br />RAM: 12 GB|
|**Mischen**<br /><br />Office, Webbrowser, Branchen Anwendungen und gelegentlich von einigen Benutzern verwendete Video Verwendung|CPU: 2C<br /><br />RAM: 2 GB|CPU: 2C<br /><br />RAM: 4 GB|CPU: 4C<br /><br />RAM: 6 GB|CPU: 4C + MT oder 6C<br /><br />RAM: 8 GB|CPU: 6C + MT<br /><br />RAM: 10 GB| CPU: 6C + MT<br /><br />RAM: 12 GB| 
|**Video intensiv**<br /><br />Office-, Webbrowser-, Branchen Anwendungen und häufig von allen Benutzern verwendete Video **Hinweise:** Videotests wurden mit dem Video "360p H. 264" bei der systemeigenen Auflösung ausgeführt.|CPU: 4C + MT<br /><br />RAM: 2 GB|CPU: 6C + MT<br /><br />RAM: 4 GB|CPU: 8C + MT<br /><br />RAM: 6 GB|CPU: 12C + MT<br /><br />RAM: 8 GB|CPU: 16C + MT<br /><br />RAM: 10 GB<br /><br />-Thin Client: RemoteFX<br />-USB-Video nicht empfehlenswert| CPU: 20C + MT<br /><br />RAM: 12 GB<br /><br />-Thin Client: RemoteFX<br />-USB-Video nicht empfehlenswert|   
  
## <a name="minimum-recommended-hardware-for-running-full-windows-10-virtual-desktops"></a>Empfohlene Hardware für die Ausführung vollständiger virtueller Windows 10-Desktops  
Das Ausführen einer vollständigen virtuellen Betriebssystem Instanz für jede Station ist Rechen intensiver als die Ausführung der standardmäßigen Multipoint Desktop-Sitzungen, sodass die Host Hardwareanforderungen pro Station höher sind:  
  
1.  CPU: 1 Kern oder Thread pro Station  
  
2.  Solid State Drive (SSD)  
  
    1.  Kapazitäts > = 20 GB pro Station + 40 GB für das WMS-Host Betriebssystem  
  
    2.  Zufälliger Lese-/Schreib-IOPS-> = 3K pro Station  
  
3.  RAM-> = 2 GB pro Station + 2 GB für das WMS-Host Betriebssystem  
  
Die BIOS-CPU-Einstellung wurde zum Aktivieren der Virtualisierung konfiguriert – Second Level Address Translation (slat)  
  
Wenden Sie sich an Ihren Hardwarehersteller, um weitere Informationen zur Auswahl der optimalen Multipoint Services-Hardware für Ihre Anforderungen zu erhalten.  