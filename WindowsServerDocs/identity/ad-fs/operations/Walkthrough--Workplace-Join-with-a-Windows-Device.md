---
ms.assetid: c17d143b-86b4-47c0-b76e-1862dda8f0bd
title: 'Exemplarische Vorgehensweise: Workplace Join mit einem Windows-Gerät'
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 9867e11aa659be9aff9912780e1186a796a7232e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71357768"
---
# <a name="walkthrough-workplace-join-with-a-windows-device"></a>Exemplarische Vorgehensweise: Arbeitsplatzbeitritt mit einem Windows-Gerät

In diesem Thema wird gezeigt, wie Sie den Arbeitsplatzbeitritt verwenden, um Ihr Windows-Gerät mit Ihrem Arbeitsplatz zu verbinden. Sie erfahren außerdem, wie Sie über das einmalige Anmelden auf eine Webanwendung zugreifen. Sie müssen die Schritte im Abschnitt [Einrichten der Lab-Umgebung für AD FS in Windows Server 2012 R2](../deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md) ausführen, bevor Sie diese exemplarische Vorgehensweise ausprobieren können.

## <a name="access-the-web-application-before-device-registration"></a>Zugriff auf die Webanwendung vor der Geräteregistrierung
In dieser exemplarischen Vorgehensweise greifen Sie auf eine Unternehmenswebanwendung zu, bevor Sie Ihr Gerät mit dem Arbeitsplatz verbinden. Auf der Webseite werden die Ansprüche angezeigt, die in Ihrem Sicherheitstoken enthalten sind. Beachten Sie, dass die Liste der Ansprüche keine Informationen zu Ihrem Gerät enthält. Möglicherweise beobachten Sie auch, dass Ihnen kein anmaliges Anmelden zur Verfügung steht.

#### <a name="to-access-the-web-application-before-you-use-workplace-join-on-your-device"></a>So greifen Sie auf die Webanwendung zu, bevor Sie den Arbeitsplatzbeitritt auf Ihrem Gerät verwenden

1. Melden Sie sich mit Ihrem Microsoft-Konto bei Client1 an.

2. Öffnen Sie Internet Explorer, und navigieren Sie zu ihrer generischen Anspruchs-APP, **https://webserv1.contoso.com/claimapp** .

3. Melden Sie sich bei der Webseite mit einem Unternehmens Domänen Konto an: <strong>roberth@contoso.com</strong>, Password: <strong>P@ssword</strong>.

4. Auf der Webseite werden alle Ansprüche in Ihrem Sicherheitstoken aufgelistet. In Ihrem Sicherheitstoken sind nur Benutzeransprüche vorhanden.

5. Schließen Sie Internet Explorer.

6. Öffnen Sie Internet Explorer, und navigieren Sie zur gleichen Anspruchs **-app, https://webserv1.contoso.com/claimapp** .

7. Beachten Sie, dass Sie aufgefordert werden, Ihre Anmeldeinformationen erneut einzugeben. Sie werden nicht mit dem Arbeitsplatz von einem Gerät mit dem Arbeitsplatzbeitritt verbunden und verfügen deshalb nicht über ein einmaliges Anmelden.

## <a name="join-your-device-with-workplace-join"></a>Hinzufügen Ihres Geräts mit dem Arbeitsplatzbeitritt

> [!IMPORTANT]
> Damit workplace Join erfolgreich ist, muss der Client Computer (CLIENT1) dem SSL-Zertifikat vertrauen, das zum Konfigurieren von Active Directory-Verbunddienste (AD FS) (AD FS) in [Schritt 2 verwendet wurde: Konfigurieren Sie den Verbund Server mit dem Geräte Registrierungsdienst (ADFS1) ](../deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md#BKMK_4). Darüber hinaus muss er die Sperrinformationen für das Zertifikat validieren können. Falls beim Arbeitsplatzbeitritt Probleme auftreten, können Sie das Ereignisprotokoll auf %%amp;quot;Client1%%amp;quot; anzeigen.
> 
> Öffnen Sie zum Anzeigen des Protokolls die Ereignisanzeige, erweitern Sie **Anwendungs- und Dienstprotokolle**, **Microsoft**und **Windows**, und klicken Sie dann auf **Arbeitsplatzbeitritt**.

#### <a name="to-join-your-device-with-workplace-join"></a>So fügen Sie Ihr Gerät mit dem Arbeitsplatzbeitritt hinzu

1. Melden Sie sich mit Ihrem Microsoft-Konto bei Client1 an.

2. Öffnen Sie auf dem Bildschirm **Start** die **Charmleiste** , und wählen Sie dann den Charm **Einstellungen** aus. Wählen Sie **PC-Einstellungen ändern** aus.

3. Wählen Sie auf der Seite **PC-Einstellungen** die Option **Netzwerk**aus, und klicken Sie dann auf **Arbeitsplatz**.

4. Geben Sie im Feld **Geben Sie Ihre Benutzer-ID ein, um Arbeitsplatz Zugriff zu erhalten oder Geräteverwaltung zu** aktivieren <strong>roberth@contoso.com</strong>ein, und klicken Sie dann auf **beitreten**.

5. Wenn Sie zur Eingabe von Anmelde Informationen aufgefordert werden, geben Sie <strong>roberth@contoso.com</strong>und Password: <strong>P@ssword</strong>ein. Klicken Sie auf **OK**.

6. Jetzt sollte die Meldung „Dieses Gerät wurde Ihrem Arbeitsplatznetzwerk hinzugefügt.“ angezeigt werden.

### <a name="access-the-web-application-after-joining-the-workplace"></a>Zugriff auf die Webanwendung nach dem Arbeitsplatzbeitritt
In diesem Teil der Demo greifen Sie von Ihrem Gerät, das mit dem Arbeitsblattbeitritt verbunden ist, auf diene Unternehmenswebanwendung zu. Auf der Webseite werden die Ansprüche angezeigt, die in Ihrem Sicherheitstoken enthalten sind. Beachten Sie, dass die Liste der Ansprüch sowohl Geräte- als auch Benutzerinformationen enthält. Möglicherweise bemerken Sie auch, dass Ihnen jetzt das einmalige Anmelden zur Verfügung steht.

##### <a name="to-access-the-web-application-after-joining-the-workplace"></a>So greifen Sie nach dem Arbeitsplatzbeitritt auf die Webanwendung zu

1. Melden Sie sich mit Ihrem Microsoft-Konto bei **Client1** an.

2. Öffnen Sie Internet Explorer, und navigieren Sie zu ihrer generischen Anspruchs-APP, **https://webserv1.contoso.com/claimapp** .

3. Melden Sie sich bei der Webseite mit einem Unternehmens Domänen Konto an: <strong>roberth@contoso.com</strong>, Password: <strong>P@ssword</strong>.

4. Auf der Webseite werden die Ansprüche in Ihrem Sicherheitstoken aufgelistet. Das Token enthält sowohl Benutzer- als auch Geräteansprüche.

5. Schließen Sie Internet Explorer.

6. Öffnen Sie Internet Explorer, und navigieren Sie zur gleichen Anspruchs **-app, https://webserv1.contoso.com/claimapp** .

7. Beachten Sie, dass Sie **nicht** aufgefordert werden, Ihre Anmeldeinformationen erneut einzugeben. Sie sind von einem Gerät mit Arbeitsplatzbeitritt verbunden und verfügen deshalb über das einmalige Anmelden.

## <a name="see-also"></a>Siehe auch
[Arbeitsplatz Beitritt von einem beliebigen Gerät für SSO und die nahtlose zweistufige Authentifizierung bei allen Unternehmensanwendungen](Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)
[Einrichten der Lab-Umgebung für AD FS in Windows Server 2012 R2](../deployment/Set-up-the-lab-environment-for-AD-FS-in-Windows-Server-2012-R2.md)
 @ no__t-4walkthrough: Arbeitsplatzbeitritt mit einem iOS-Gerät](Walkthrough--Workplace-Join-with-an-iOS-Device.md)



