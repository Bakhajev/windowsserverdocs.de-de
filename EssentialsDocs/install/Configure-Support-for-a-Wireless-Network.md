---
title: Konfigurieren der Unterstützung für ein Funknetzwerk
description: Beschreibt, wie Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d7020d4-fd46-4858-a406-de5c0f21ea06
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: c5c98727b81bf37fdb3f90c612270462a51908c8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59833111"
---
# <a name="configure-support-for-a-wireless-network"></a>Konfigurieren der Unterstützung für ein Funknetzwerk

>Gilt für: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Sie können das Betriebssystem zur Unterstützung eines Funknetzwerks konfigurieren. Die folgenden Anforderungen müssen erfüllt sein, damit auf dem Server die Funkunterstützung aktiviert werden kann:  
  
-   Auf dem Server muss ein Adapter für Funknetzwerke installiert sein.  
  
-   Wenn der Netzwerkadapter vom Betriebssystem nicht unterstützt wird, muss für den Adapter für Funknetzwerke der richtige Treiber vorinstalliert werden.  
  
-   Es muss die Möglichkeit bestehen, den Adapter für Funktnetzwerke zu aktivieren und zu deaktivieren. Dies kann über eine Taste am Server oder eine benutzerdefinierte Benutzeroberfläche im Dashboard erfolgen. Das Produkthandbuch sollte die Schritte zum Aktivieren und Deaktivieren des Adapter für Funknetzwerke enthalten.  
  
-   Es muss die Möglichkeit bestehen, ein Funknetzwerk auszuwählen und eine Verbindung mit diesem herzustellen. Zu diesem Zweck wird dem Dashboard am besten eine benutzerdefinierte Benutzeroberfläche hinzugefügt. Im Produkthandbuch sollten die Schritte zum Auswählen eines Funknetzwerks sowie zum Herstellen einer Verbindung mit diesem aufgeführt sein.  
  
-   Wenn die Möglichkeit der Unterstützung eines Ad-hoc-Funknetzwerks bestehen muss, muss eine erweiterte Benutzeroberfläche im Dashboard bereitgestellt werden. Bei der Benutzeroberfläche kann es sich um eine Schaltfläche oder einen Link handeln, über die bzw. den der Assistent zum Einrichten eines Ad-hoc-Funknetzwerks in der Systemsteuerung in Windows Server 2008 R2 gestartet wird.  
  
## <a name="additional-considerations"></a>Weitere Aspekte  
 Ziehen Sie beim Konfigurieren der Unterstützung für ein Funknetzwerk auch folgende Informationen in Betracht:  
  
-   Der Server muss über ein Kabel mit dem Netzwerk verbunden sein, damit Setup ausgeführt werden kann.  
  
-   Ein Netzwerkcomputer, auf dem eine Bare-Metal-Recovery ausgeführt wird, muss über ein Kabel mit dem Netzwerk verbunden sein.  
  
-   Der Server muss über ein Kabel mit dem Netzwerk verbunden sein, damit auf dem Server eine Bare-Metal-Recovery ausgeführt werden kann.  
  
-   Wenn auf dem Server ein Ad-hoc-Netzwerk erstellt wird, ist der Adapter für Funknetzwerke für das Ad-hoc-Netzwerk vorgesehen, sodass der Benutzer immer das Netzwerkkabel mit dem Server verbinden muss, um eine Internetverbindung herzustellen.  
  
> [!NOTE]
>  Weitere Informationen zum Konfigurieren von Netzwerkverbindungen finden Sie unter [Vorkonfigurieren eines Routers](Preconfiguring-a-Router.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Anpassen des Abbilds](Creating-and-Customizing-the-Image.md)   
 [Zusätzliche Anpassungen](Additional-Customizations.md)   
 [Vorbereiten des Abbilds für die Bereitstellung](Preparing-the-Image-for-Deployment.md)   
 [Testen der Benutzerfreundlichkeit](Testing-the-Customer-Experience.md)