---
title: Multipoint Services-Benutzerkonten
description: Erfahren Sie mehr über Benutzerkonten in Multipoint Services, insbesondere die für verschiedene Szenarien zu verwendende Art.
ms.custom: na
ms.prod: windows-server
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7f3c6ce5-9b7c-45a0-83c5-3f9b9f5f48d4
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: ff81af2a0aa8da7f801ec14c27dc00c9bae6e8aa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71388959"
---
# <a name="example-scenarios-multipoint-services-user-accounts"></a>Beispielszenarien: Multipoint Services-Benutzerkonten
Was müssen Sie tun, um das Benutzerkonto Szenario zu implementieren, das Sie für Ihre Multipoint Services-Umgebung ausgewählt haben? In den folgenden Tabellen werden die einzelnen Aufgaben beschrieben, die zum Konfigurieren von Benutzerkonten und zum Vorbereiten von Stationen für freigegebene oder einzelne Benutzerkonten auf einem eigenständigen Multipoint-Computer oder auf Netzwerkservern in einer Arbeitsgruppe oder einer Active Directory Domäne durchgeführt werden. Wählen Sie das Szenario aus, das für Ihre Umgebung gilt. Folgen Sie dann den Links in der Tabelle, um die einzelnen erforderlichen Konfigurationsaufgaben abzuschließen.  
  
> [!NOTE]  
> Wenn Sie noch nicht entschieden haben, wie Sie Ihre Benutzerkonten einrichten, finden Sie unter [Planen von Benutzerkonten für Ihre Multipoint Services-Umgebung](Plan-user-accounts-for-your-MultiPoint-services-environment.md) Weitere Informationen dazu, wie sich die einzelnen Auswahl auf die Benutzer auswirken.  
  
## <a name="single-multipoint-services-computer-in-a-stand-alone-environment-no-network"></a>Einzelner Multipoint Services-Computer in einer eigenständigen Umgebung (kein Netzwerk)  
  
|||  
|-|-|  
|**Meine Benutzer müssen sich nicht anmelden.** Die Stationen können allen Benutzern zur Verfügung stehen. Sie benötigen keine individuelle Windows-Desktop Darstellung, die private Ordner zum Speichern von Daten oder personalisierten Desktops umfasst.|1.  Erstellen Sie ein einzelnes lokales Benutzerkonto (Anweisungen hierzu finden Sie unter [Erstellen von lokalen Benutzerkonten](Create-local-user-accounts.md)).<br />2.  [Zulassen mehrerer Sitzungen für ein Konto](Allow-one-account-to-have-multiple-sessions.md)<br />3.  [Konfigurieren von Stationen für die automatische Anmeldung](Configure-stations-for-automatic-logon.md)|  
|**Meine Benutzer können die gleiche Benutzeranmeldung verwenden.** Sie benötigen keine individuelle Windows-Desktop Darstellung, die private Ordner zum Speichern von Daten oder personalisierten Desktops umfasst.|1.  Erstellen Sie ein einzelnes lokales Benutzerkonto (Anweisungen hierzu finden Sie unter [Erstellen von lokalen Benutzerkonten](Create-local-user-accounts.md)).<br />2.  [Zulassen mehrerer Sitzungen für ein Konto](Allow-one-account-to-have-multiple-sessions.md)|  
|**Meine Benutzer müssen über eine eigene Windows-Desktop Darstellung verfügen.**|Erstellen Sie ein lokales Benutzerkonto für jeden Benutzer (Anweisungen hierzu finden Sie unter [Erstellen von lokalen Benutzerkonten](Create-local-user-accounts.md)).|  
  
## <a name="multiple-multipoint-services-computers-on-a-network-but-with-no-domain"></a>Mehrere Multipoint Services-Computer in einem Netzwerk, aber ohne Domäne  
  
|||  
|-|-|  
|**Meine Benutzer müssen sich nicht anmelden.** Die Stationen können allen Benutzern zur Verfügung stehen. Sie benötigen keine individuelle Windows-Desktop Darstellung, die private Ordner zum Speichern von Daten oder personalisierten Desktops umfasst.|1.  Erstellen Sie ein einzelnes lokales Benutzerkonto auf jedem Server. (Anweisungen hierzu finden Sie unter [Erstellen von lokalen Benutzerkonten](Create-local-user-accounts.md).)<br />2.  [Einem Konto erlauben, mehrere Sitzungen](Allow-one-account-to-have-multiple-sessions.md) auf jedem Server zu haben<br />3.  [Konfigurieren von Stationen für die automatische Anmeldung](Configure-stations-for-automatic-logon.md) auf jedem Server|  
|**Meine Benutzer können die gleiche Benutzeranmeldung verwenden.** Sie benötigen keine individuelle Windows-Desktop Darstellung, die private Ordner zum Speichern von Daten oder personalisierten Desktops umfasst.|1.  Erstellen Sie ein einzelnes lokales Benutzerkonto auf jedem Server. (Anweisungen hierzu finden Sie unter [Erstellen von lokalen Benutzerkonten](Create-local-user-accounts.md).)<br />2.  [Erlauben Sie einem Konto, mehrere Sitzungen](Allow-one-account-to-have-multiple-sessions.md) auf jedem Server zu haben.|  
|**Meine Benutzer müssen über eine eigene Windows-Desktop Darstellung verfügen.**<br /><br />-   **Option A** -meine Benutzer verwenden immer lokale Stationen, die mit demselben Multipoint Services-Computer verbunden sind.<br />-   **Option B** : meine Benutzer verwenden lokale Stationen auf mehr als einem Multipoint Services-Computer.<br />-   **Option C** : meine Benutzer verwenden Remote Clients im LAN.|-   **Option A** : Erstellen Sie auf jedem Server ein einzelnes lokales Benutzerkonto für die Benutzer dieses Servers. (Anweisungen hierzu finden Sie unter [Erstellen von lokalen Benutzerkonten](Create-local-user-accounts.md).)<br />-   **Option B** : Erstellen Sie lokale Benutzerkonten für jeden Benutzer auf jedem Server. **Hinweis**: Dies bedeutet, dass jeder Benutzer über ein Profil auf jedem Server verfügt. Anders ausgedrückt: Wenn eine Datei in "eigene Dokumente" gespeichert wird, während Sie bei der Station von Server a angemeldet ist, wird die Datei bei der Anmeldung bei Server B nicht angezeigt. (Anweisungen hierzu finden Sie unter [Erstellen von lokalen Benutzerkonten](Create-local-user-accounts.md).)<br />-   **Option C** : weisen Sie jeden Benutzer einem bestimmten Multipoint Services-Computer zu. Erstellen Sie lokale Benutzerkonten für die zugewiesenen Benutzer auf jedem Server. (Anweisungen hierzu finden Sie unter [Erstellen von lokalen Benutzerkonten](Create-local-user-accounts.md).)|  
  
## <a name="one-or-more-multipoint-services-computers-in-a-domain-network-environment"></a>Mindestens ein Multipoint Services-Computer in einer Domänen Netzwerkumgebung  
  
|||  
|-|-|  
|**Meine Benutzer müssen sich nicht anmelden.** Die Stationen können allen Benutzern zur Verfügung stehen. Sie benötigen keine individuelle Windows-Desktop Darstellung, die private Ordner zum Speichern von Daten oder personalisierten Desktops umfasst.|1.  Erstellen Sie ein Domänen Konto, um sich bei den Servern anzumelden.<br />2.  [Erlauben Sie einem Konto, mehrere Sitzungen](Allow-one-account-to-have-multiple-sessions.md) auf jedem Server zu haben.<br />3.  [Konfigurieren Sie Stationen für die automatische Anmeldung](Configure-stations-for-automatic-logon.md) auf den einzelnen Servern.|  
|**Meine Benutzer können die gleiche Benutzeranmeldung verwenden.** Sie benötigen keine individuelle Windows-Desktop Darstellung, die private Ordner zum Speichern von Daten oder personalisierten Desktops umfasst.|1.  Erstellen Sie ein Domänen Konto für eine Gruppe oder für jeden Benutzer.<br />2.  [Erlauben Sie einem Konto, mehrere Sitzungen](Allow-one-account-to-have-multiple-sessions.md) auf jedem Server zu haben.|  
|**Meine Benutzer müssen über eine eigene Windows-Desktop Darstellung verfügen.**<br /><br />-   **Option A** : jeder Benutzer mit einem Domänen Konto kann den Multipoint Services-Computer verwenden.<br />-   **Option B** : Ich möchte einschränken, welche Domänen Konten auf den Server zugreifen können.|-   **Option A** : Es ist kein Setup erforderlich. Standardmäßig haben alle Domänen Benutzer Zugriff auf alle Multipoint Services-Computer im Netzwerk.<br />-   **Option B** : schränken Sie den Zugriff von Domänen Benutzerkonten auf den Multipoint Services-Computer ein. Anweisungen hierzu finden [Sie unter Einschränken des Benutzer Zugriffs auf den Server](limit-users--access-to-the-server-in-multipoint-services.md).|  
|**Ich möchte lokale Benutzerkonten verwenden und diese separat von meinen Domänen Konten verwalten.** Angenommen, Sie möchten, dass eine Person Multipoint Services, aber nicht die Domäne verwaltet, oder Sie möchten Domänen Konten nicht allen Multipoint Services-Benutzern zur Verfügung stellen.|Erstellen Sie ein oder mehrere lokale Benutzerkonten auf jedem Server. (Anweisungen hierzu finden Sie unter [Erstellen von lokalen Benutzerkonten](Create-local-user-accounts.md).)<br /><br />**Hinweis**: Dies bedeutet, dass jedes Benutzerkonto ein Profil auf jedem Server hat. Anders ausgedrückt: Wenn eine Datei in "eigene Dokumente" gespeichert wird, während Sie bei der Station von Server a angemeldet ist, wird die Datei bei der Anmeldung bei Server B nicht angezeigt.|  