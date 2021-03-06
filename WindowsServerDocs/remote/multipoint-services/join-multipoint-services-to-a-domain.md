---
title: Verknüpfen von Multipoint Services mit einer Domäne (optional)
Description: Enthält die Schritte zum Verknüpfen von Multipoint Services mit Ihrer Domäne.
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 623b7c21-dcbb-402e-8b5a-8e434cd225bd
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: 79bd9e594f94c7b3acd06265891dd646b3853b50
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71394743"
---
# <a name="join-the-multipoint-services-computer-to-a-domain-optional"></a>Hinzufügen des Multipoint Services-Computers zu einer Domäne (optional)
Wenn Sie über eine Active Directory Domäne auf den Multipoint Services-Computer zugreifen werden, besteht der nächste Schritt darin, den Computer der Domäne hinzuzufügen.  
  
> [!IMPORTANT]  
> Sie müssen die Zeitzone überprüfen, bevor Sie den Computer einer Domäne hinzufügen. Anweisungen finden Sie unter [Festlegen von Datum, Uhrzeit und](Set-the-date--time--and-time-zone.md)Zeitzone.  
   
1.  Öffnen Sie auf der **Startseite die ****Systemsteuerung**. Klicken Sie auf **System und Sicherheit**, und klicken Sie dann auf **System**.  
  
2.  Klicken Sie unter **Einstellungen für Computernamen, Domäne und Arbeitsgruppe**auf **Einstellungen ändern**.  
  
3.  Klicken Sie auf der Registerkarte **Computer Name** auf **ändern**.  
  
4.  Wählen Sie im Dialogfeld **Computer Name/Domänen Änderungen** die Option **Domäne**aus, geben Sie den Namen der Domäne ein, und klicken Sie dann auf **OK**. führen Sie dann die Schritte im Assistenten aus, um den Vorgang abzuschließen.  
  
5.  Melden Sie sich nach dem Neustart des Computers als Administrator an, und warten Sie, bis der Multipoint-Manager geöffnet wird.  
  
> [!IMPORTANT]  
> Um sicherzustellen, dass die Bereitstellung der Multipoint Services-Domäne ordnungsgemäß funktioniert, müssen Sie einige Gruppenrichtlinien konfigurieren und die Registrierung aktualisieren. Weitere Informationen finden Sie unter [Konfigurieren von Gruppenrichtlinien für eine Domänen Bereitstellung](https://technet.microsoft.com/library/dn265982.aspx).  