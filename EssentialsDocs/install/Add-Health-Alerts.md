---
title: Hinzufügen von Integritätswarnungen
description: Beschreibt, wie Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 270e0aac-dc42-46f3-a20b-a68ffbded06d
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 8c3ba4746211690ad52f775b8bdc1ccf9b6c74b7
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433726"
---
# <a name="add-health-alerts"></a>Hinzufügen von Integritätswarnungen

>Gilt für: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Ein Integritäts-Add-In bietet Definitionen für Warnungen, Integritätsprüfungen und Reparaturen für Netzwerkprobleme. Ein Integritäts-Add-In besteht aus XML-Dateien, mit denen Codeausschnitte oder Daten kommentiert werden, die zum Bewerten der Integritätsinformationen für ein bestimmtes Feature dienen. Integritäts-Add-Ins werden von Entwicklern erstellt und vom Administrator auf dem Server und den Clientcomputern installiert.  
  
 Details zum Erstellen eines Integritäts-Add-Ins finden Sie im [SDK für Windows Server-Lösungen](https://go.microsoft.com/fwlink/?LinkID=248648) .  
  
## <a name="installing-health-add-in-files"></a>Installieren von Dateien für Integritäts-Add-Ins  
 Nachdem der Entwickler die XML-Dateien erstellt hat, müssen Sie eine Kopie der Dateien am entsprechenden Speicherort auf dem Server und den Clientcomputern platzieren.  
  
#### <a name="to-install-the-xml-files-on-the-server"></a>So installieren Sie die XML-Dateien auf dem Server  
  
1. Erstellen Sie einen neuen Ordner mit dem Namen **MyHealthAddIn** im Ordner **%ProgramFiles%\Windows Server\Bin\Feature Definitions**. Sie können diesem Ordner einen beliebigen Namen geben. Es ist von Vorteil, wenn der Ordnernamen und der Funktionsname identisch sind.  
  
2. Kopieren Sie die Dateien "Definition.xml" und "Definition.xml.config" in den neuen Ordner.  
  
3. Wenn Sie Binärdateien für Bedingungen oder Aktionen erstellt haben, sollten Sie diese Dateien auch nach **%ProgramFiles%\Windows Server\Bin** kopieren.  
  
   Clientcomputer führen alle 6 Stunden eine geplante Aufgabe aus, mit der die XML-Dateien an den entsprechenden Speicherort kopiert werden. Sie können die Synchronisierung zwischen dem Clientcomputer und dem Server erzwingen, indem Sie die Aufgabe manuell ausführen.  
  
#### <a name="to-install-the-xml-files-on-the-client-computer"></a>So installieren Sie die XML-Dateien auf dem Clientcomputer  
  
1.  Öffnen Sie die Aufgabenplanung.  
  
2.  Führen Sie in der Aufgabenplanung **HealthDefintionUpdateTask** aus.  
  
    > [!NOTE]
    >  Mit dieser Aufgabe werden keine Binärdateien installiert. Sie müssen die Binärdateien manuell in den Ordner **%ProgramFiles%\Windows Server\Bin** auf dem Clientcomputer kopieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen und Anpassen des Abbilds](Creating-and-Customizing-the-Image.md)   
 [Zusätzliche Anpassungen](Additional-Customizations.md)   
 [Vorbereiten des Abbilds für die Bereitstellung](Preparing-the-Image-for-Deployment.md)   
 [Testen der Benutzerfreundlichkeit](Testing-the-Customer-Experience.md)