---
title: Erstellen der Datei "PostIC.cmd" zum Ausführen von Aufgaben nach der Erstkonfiguration
description: Beschreibt, wie Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99e258bc-0695-48c9-b694-a7f3cbe2a2d0
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: e15cb8591fc701094dde884d0a55e08d2cf422bb
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433598"
---
# <a name="create-the-posticcmd-file-for-running-post-initial-configuration-tasks"></a>Erstellen der Datei "PostIC.cmd" zum Ausführen von Aufgaben nach der Erstkonfiguration

>Gilt für: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Sie können Anpassungen nach der Erstkonfiguration hinzufügen, indem Sie Ihren eigenen Code schreiben und anschließend diesen Code über eine Skriptdatei mit der Bezeichnung "PostIC.cmd" aufrufen. Bei der Verwendung der Datei "PostIC.cmd" müssen Sie die folgenden Richtlinien befolgen:  
  
- Der Anpassungscode muss im Hintergrund ausgeführt werden (Anzeige einer Benutzeroberfläche ist nicht möglich).  
  
- Durch den Anpassungscode kann kein Neustart des Servers initiiert werden. Die Erstkonfiguration startet den Server im letzten Task neu.  
  
- Die Ausführung des Anpassungscodes darf höchstens drei Minuten dauern.  
  
  Definieren Sie die Datei "PostIC.cmd" so, dass "0" zurückgegeben wird, wenn der Code erfolgreich ausgeführt wurde. Wenn ein anderer Wert zurückgegeben wird, sucht das Betriebssystem nach einer Datei namens [SetupFailure.cmd](Create-the-PostIC.cmd-File-for-Running-Post-Initial-Configuration-Tasks.md#BKMK_SetupFailure), in der Code enthalten ist, der auszuführen ist, wenn der Code in der Datei „PostIC.cmd“ nicht erfolgreich ausgeführt wurde. Die Datei "PostIC.cmd" und die Datei "SetupFailure.cmd" müssen sich unter folgendem Pfad befinden: "C:\Windows\Setup\Scripts".  
  
#### <a name="to-define-post-initial-configuration-customizations"></a>So definieren Sie Anpassungen nach der Erstkonfiguration  
  
1.  Schreiben Sie den Code, der von dem Skript "PostIC.cmd" aufgerufen wird.  
  
2.  Erstellen Sie in Editor eine Datei namens "PostIC.cmd", und fügen Sie dieser den Aufruf des in Schritt 1 erstellten Codes hinzu. Stellen Sie sicher, dass der Code einen Wert zurückgibt, der angibt, dass der Vorgang erfolgreich ausgeführt wurde.  
  
3.  Speichern Sie die Datei "PostIC.cmd" unter "C:\Windows\Setup\Scripts".  
  
4.  (Optional) Erstellen Sie eine Datei namens "SetupFailure.cmd", die Code ausführt, falls "PostIC.cmd" einen anderen Wert als "0" zurückgibt.  
  
###  <a name="BKMK_SetupFailure"></a> SetupFailure.cmd  
 Mithilfe der Datei "SetupFailure.cmd" können Sie Benachrichtigungen zu Problemen bei der Erstkonfiguration angeben. Die Datei "SetupFailure.cmd" enthält den Code, den Sie beim Auftreten von Problemen ausführen können. Die Datei "SetupFailure.cmd" befindet sich unter "C:\Windows\Setup\Scripts" und wird ausgeführt, wenn bei einem Setuptask ein Problem auftritt oder wenn die Datei "PostIC.cmd" einen anderen Wert als "0" zurückgibt.  
  
##### <a name="to-define-notifications"></a>So definieren Sie Benachrichtigungen  
  
1.  Schreiben Sie den Code, der vom Skript "SetupFailure.cmd" aufgerufen wird.  
  
2.  Erstellen Sie im Editor eine Datei namens "SetupFailure.cmd", und fügen Sie dieser den Aufruf des in Schritt 1 erstellten Codes hinzu. Stellen Sie sicher, dass der Code einen Wert zurückgibt, der angibt, dass der Vorgang erfolgreich ausgeführt wurde.  
  
3.  Speichern Sie die Datei "SetupFailure.cmd" unter "C:\Windows\Setup\Scripts".  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte mit Windows Server Essentials ADK](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Erstellen und Anpassen des Abbilds](Creating-and-Customizing-the-Image.md)   
 [Zusätzliche Anpassungen](Additional-Customizations.md)   
 [Vorbereiten des Abbilds für die Bereitstellung](Preparing-the-Image-for-Deployment.md)   
 [Testen der Benutzerfreundlichkeit](Testing-the-Customer-Experience.md)