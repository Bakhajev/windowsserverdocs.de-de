---
title: Schritt 4 Planen von OTP auf dem Remote Zugriffs Server
description: Dieses Thema ist Teil des Handbuchs Bereitstellen des Remote Zugriffs mit OTP-Authentifizierung in Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b97b2fd-767a-45c1-a64e-5b3edd0c8a47
ms.author: pashort
author: shortpatti
ms.openlocfilehash: cc833ea2ae5d24754a445d6c1252f21a59cc6f13
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404384"
---
# <a name="step-4-plan-for-otp-on-the-remote-access-server"></a>Schritt 4 Planen von OTP auf dem Remote Zugriffs Server

>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016

Nach der Planung der Server-und Zertifikat Einstellungen für das einmalige Kennwort (One-time password, OTP) müssen Sie den letzten Schritt bei der Planung einer Bereitstellung für den Remote Zugriff auf den RAS-Server planen.  
  
|Aufgabe|Beschreibung|  
|----|--------|  
|[4,1 Planen von OTP-Client Ausnahmen](#bkmk_4_1_Exemptions)|Planen Sie Ausnahmen für Benutzer ein, die für die Authentifizierung mit OTP nicht erforderlich sind.|  
|[4,2 Planen für Windows 7-Clients](#bkmk_4_2_Win7)|Planen Sie die Bereitstellung des DirectAccess-konnektivitätsassistenten (DCA) 2,0 für Windows 7-Client Computer.|  
|[4,3 Planen von Smartcards](#BKMK_smartcard)|Planen Sie die Verwendung von Smartcards für zusätzliche Autorisierung.|  
  
## <a name="bkmk_4_1_Exemptions"></a>4,1 Planen von OTP-Client Ausnahmen  
Wenn die OTP-Authentifizierung aktiviert ist, müssen sich alle Benutzer standardmäßig mit einer Kombination aus Benutzername und Kennwort und OTP-Anmelde Informationen authentifizieren. Allerdings können Sie es Benutzern ermöglichen, sich nur mit einem Benutzernamen und einem Kennwort zu authentifizieren, ohne OTP zu verwenden. Erstellen Sie dazu eine Sicherheitsgruppe, und fügen Sie alle Benutzer hinzu, die von der OTP-Authentifizierung ausgenommen werden sollen.  
  
> [!NOTE]  
> Nur Client Computer aus einer einzelnen Gesamtstruktur können aufgrund der Tatsache, dass nur eine Sicherheitsgruppe für Client Ausnahmen ausgewählt werden kann, ausgenommen werden.  
  
## <a name="bkmk_4_2_Win7"></a>4,2 Planen für Windows 7-Clients  
Windows 7-Client Computer können sich standardmäßig nicht mithilfe von OTP authentifizieren.  Windows 7-Client Computer erfordern eine DCA 2,0 für die Authentifizierung mithilfe von OTP in einer Windows Server 2012-Remote Zugriffs Bereitstellung. Weitere Informationen zu DCA 2,0 finden Sie unter [DirectAccess Connectivity Assistant 2,0](https://go.microsoft.com/fwlink/?LinkId=253699) im Microsoft Download Center.  
  
## <a name="BKMK_smartcard"></a>4,3 Planen von Smartcards  
Wenn die OTP-Authentifizierung aktiviert ist, ist die Option zum Aktivieren der Verwendung von Smartcards für zusätzliche Autorisierung verfügbar. Erstellen Sie eine Sicherheitsgruppe, um vorübergehenden Zugriff zuzulassen, falls die Smartcard eines Benutzers nicht funktionsfähig ist.  
  
## <a name="BKMK_Links"></a>Siehe auch  
  
-   [Konfigurieren von DirectAccess mit OTP-Authentifizierung](https://technet.microsoft.com/windows-server-docs/networking/remote-access/ras/otp/deploy-ra-otp)  
  


