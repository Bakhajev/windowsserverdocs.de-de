---
title: Übersicht über Always on VPN-Technologie
description: 'Auf dieser Seite wird eine kurze Übersicht über die Always on VPN-Technologien mit Links zu ausführlichen Dokumenten bereitgestellt. '
ms.prod: windows-server
ms.technology: networking-ras
ms.topic: article
ms.date: 11/05/2018
ms.author: pashort
author: shortpatti
ms.localizationpriority: medium
ms.openlocfilehash: 31d0d5c12760fc627ce93972f4a70e85f61dd178
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404370"
---
# <a name="always-on-vpn-technology-overview"></a>Übersicht über Always on VPN-Technologie

>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016, Windows Server 2012 R2, Windows 10

- [**Vorher** Weitere Informationen zu den Always on-VPN-Erweiterungen](always-on-vpn-enhancements.md)
- [**Weiter** Erfahren Sie mehr über die erweiterten Features von Always on VPN](deploy/always-on-vpn-adv-options.md)

Für diese Bereitstellung müssen Sie einen neuen RAS-Server installieren, auf dem Windows Server 2016 ausgeführt wird. Außerdem müssen Sie einen Teil der vorhandenen Infrastruktur für die Bereitstellung ändern.

Die folgende Abbildung zeigt die Infrastruktur, die für die Bereitstellung Always on VPN erforderlich ist.

![Always on VPN-Infrastruktur](../../../media/Always-On-Vpn/Ao-Vpn-Overview.jpg)

Der in dieser Abbildung dargestellte Verbindungsprozess besteht aus den folgenden Schritten:

1. Mit öffentlichen DNS-Servern führt der Windows 10-VPN-Client eine namens Auflösungs Abfrage für die IP-Adresse des VPN-Gateways aus.

2. Mithilfe der von DNS zurückgegebenen IP-Adresse sendet der VPN-Client eine Verbindungsanforderung an das VPN-Gateway.

3. Das VPN-Gateway wird auch als Remote Authentication Dial-in User Service (RADIUS)-Client konfiguriert. der VPN-RADIUS-Client sendet die Verbindungsanforderung für die Verarbeitung von Verbindungsanforderungen an den NPS-Server der Organisation/des Unternehmens.

4. Der NPS-Server verarbeitet die Verbindungsanforderung, einschließlich der Autorisierung und Authentifizierung, und bestimmt, ob die Verbindungsanforderung zugelassen oder verweigert wird.

5. Der NPS-Server leitet eine Access-Accept-oder Access-Deny-Antwort an das VPN-Gateway weiter.

6. Die Verbindung wird basierend auf der Antwort, die der VPN-Server vom NPS-Server empfangen hat, initiiert oder beendet.

Weitere Informationen zu den einzelnen Infrastrukturkomponenten, die in der obigen Abbildung dargestellt werden, finden Sie in den folgenden Abschnitten.

>[!NOTE]
>Wenn Sie bereits einige dieser Technologien in Ihrem Netzwerk bereitgestellt haben, können Sie die Anweisungen in diesem Bereitstellungs Leit Faden verwenden, um eine zusätzliche Konfiguration der Technologien für diesen Bereitstellungs Zweck auszuführen.

## <a name="domain-name-system-dns"></a>Domain Name System (DNS)

Sowohl interne als auch externe Domain Name System (DNS-Zonen) sind erforderlich. dabei wird davon ausgegangen, dass die interne Zone eine delegierte Unterdomäne der externen Zone ist (z. b. Corp.contoso.com und contoso.com).

Erfahren Sie mehr über [Domain Name System (DNS)](../../../../networking/dns/dns-top.md) oder das Haupt [Netzwerk Handbuch](../../../../networking/core-network-guide/core-network-guide.md).

>[!NOTE]
>Andere DNS-Entwürfe, z. b. Split-Brain-DNS (mit dem gleichen Domänen Namen intern und extern in separaten DNS-Zonen) oder nicht verknüpfte interne und externe Domänen (z. b. Conto. local und contoso.com) sind ebenfalls möglich. Weitere Informationen zum Bereitstellen von Split-Brain-DNS finden Sie unter [Verwenden der DNS-Richtlinie für Split-Brain-DNS-Bereitstellung](../../../../networking/dns/deploy/split-brain-DNS-deployment.md)

## <a name="firewalls"></a>Firewalls

Stellen Sie sicher, dass die Firewalls zulassen, dass der Datenverkehr, der für die VPN-und RADIUS-Kommunikation erforderlich ist, richtig funktioniert.

Weitere Informationen finden Sie unter [Konfigurieren von Firewalls für RADIUS-Datenverkehr](../../../../networking/technologies/nps/nps-firewalls-configure.md).

## <a name="remote-access-as-a-ras-gateway-vpn-server"></a>Remote Zugriff als RAS-Gateway-VPN-Server

In Windows Server 2016 ist die Remote Zugriffs-Server Rolle so konzipiert, dass Sie sowohl einen Router als auch einen RAS-Server ausführt. Daher unterstützt es eine Vielzahl von Features. Für diese Anleitung für die Bereitstellung benötigen Sie nur eine kleine Teilmenge dieser Features: Unterstützung für IKEv2-VPN-Verbindungen und LAN-Routing.

IKEv2 ist ein VPN-Tunnelingprotokoll, das in Internet Engineering Task Force Request for Comments 7296 beschrieben wird. Der Hauptvorteil von IKEv2 besteht darin, dass Unterbrechungen in der zugrunde liegenden Netzwerkverbindung toleriert werden. Wenn beispielsweise die Verbindung vorübergehend unterbrochen wird oder ein Benutzer einen Client Computer von einem Netzwerk auf einen anderen verschiebt, stellt IKEv2 die VPN-Verbindung automatisch wieder her, wenn die Netzwerkverbindung wieder hergestellt wird – ohne Benutzereingriff.

Mithilfe des RAS-Gateways können Sie VPN-Verbindungen bereitstellen, um Endbenutzern Remote Zugriff auf das Netzwerk und die Ressourcen Ihrer Organisation zu bieten. Wenn Remote Computer mit dem Internet verbunden sind, wird bei der Bereitstellung Always on VPN eine permanente Verbindung zwischen Clients und Ihrem Organisations Netzwerk aufrechterhalten. Mit dem RAS-Gateway können Sie auch eine Site-to-Site-VPN-Verbindung zwischen zwei Servern an unterschiedlichen Standorten erstellen, z. b. zwischen Ihrer primären Niederlassung und einer Zweigstelle, und die Netzwerk Adressübersetzung (Network Address Translation, NAT) verwenden, damit Benutzer im Netzwerk auf extern zugreifen können. Ressourcen, z. b. das Internet. Außerdem unterstützt das RAS-Gateway Border Gateway Protocol (BGP), das dynamische Routing Dienste bereitstellt, wenn Ihre Remote Niederlassungen auch Edge-Gateways aufweisen, die BGP unterstützen.

RAS-Gateways können mithilfe von Windows PowerShell-Befehlen und der Microsoft Management Console (MMC) für den Remote Zugriff verwaltet werden.

## <a name="network-policy-server-nps"></a>Netzwerkrichtlinienserver (Network Policy Server, NPS)

Mit NPS können Sie Organisations weite Netzwerk Zugriffsrichtlinien für die Authentifizierung und Autorisierung von Verbindungsanforderungen erstellen und erzwingen. Wenn Sie NPS als RADIUS-Server (Remote Authentication Dial-in User Service) verwenden, konfigurieren Sie Netzwerk Zugriffs Server, z. b. VPN-Server, als RADIUS-Clients in NPS.

Sie können auch Netzwerkrichtlinien konfigurieren, mit denen NPS Verbindungsanforderungen autorisiert, und Sie können die RADIUS-Kontoführung so konfigurieren, dass NPS Kontoführungsinformationen in Protokolldateien auf der lokalen Festplatte oder in einer Microsoft SQL Server-Datenbank protokolliert.

Weitere Informationen finden Sie unter [Netzwerk Richtlinien Server (Network Policy Server, NPS)](../../../../networking/technologies/nps/nps-top.md).

## <a name="active-directory-certificate-services"></a>Active Directory-Zertifikatdienste

Der Server der Zertifizierungsstelle (Certification Authority, ca) ist eine Zertifizierungsstelle, die Active Directory Zertifikat Dienste ausgeführt wird. Für die VPN-Konfiguration ist eine Active Directory basierte Public Key-Infrastruktur (PKI) erforderlich.

Organisationen können AD CS verwenden, um die Sicherheit zu erhöhen, indem Sie die Identität einer Person, eines Geräts oder Diensts an einen entsprechenden öffentlichen Schlüssel binden. AD CS umfasst auch Features, mit denen Sie die Zertifikat Registrierung und die Sperrung in einer Vielzahl von skalierbaren Umgebungen verwalten können. Weitere Informationen finden Sie unter [Übersicht über Active Directory Zertifikat Dienste](https://technet.microsoft.com/library/hh831740.aspx) und [Entwurfs Leit Fäden für die Public Key-Infrastruktur](https://social.technet.microsoft.com/wiki/contents/articles/2901.public-key-infrastructure-design-guidance.aspx).

Während der Fertigstellung der Bereitstellung konfigurieren Sie die folgenden Zertifikat Vorlagen für die Zertifizierungsstelle.

- Die Zertifikat Vorlage für die Benutzerauthentifizierung

- Die Zertifikat Vorlage für die VPN-Server Authentifizierung

- Die Zertifikat Vorlage für die NPS-Server Authentifizierung

### <a name="certificate-templates"></a>Zertifikatvorlagen

Zertifikat Vorlagen können die Verwaltung einer Zertifizierungsstelle (Certification Authority, ca) erheblich vereinfachen, da Sie Zertifikate ausstellen können, die für ausgewählte Tasks vorkonfiguriert sind. Mit dem MMC-Snap-in "Zertifikat Vorlagen" können Sie die nachfolgend aufgeführten Aufgaben ausführen.

- Anzeigen der Eigenschaften für jede Zertifikat Vorlage.

- Kopieren und ändern Sie Zertifikat Vorlagen.

- Steuern Sie, welche Benutzer und Computer Vorlagen lesen und für Zertifikate registrieren können.

- Ausführen weiterer Verwaltungsaufgaben im Zusammenhang mit Zertifikat Vorlagen

Zertifikat Vorlagen sind ein wesentlicher Bestandteil einer Unternehmens Zertifizierungsstelle (Certification Authority, ca). Sie sind ein wichtiges Element der Zertifikat Richtlinie für eine-Umgebung, die den Satz von Regeln und Formaten für die Zertifikat Registrierung,-Verwendung und-Verwaltung ist.

Weitere Informationen finden Sie unter [Zertifikat Vorlagen](https://technet.microsoft.com/library/cc730705.aspx).

### <a name="digital-server-certificates"></a>Zertifikate für digitale Server

Dieser Leitfaden zur Bereitstellung enthält Anweisungen für die Verwendung von Active Directory Zertifikat Diensten (AD CS) zum Registrieren und automatischen Registrieren von Zertifikaten für RAS-und NPS-Infrastruktur Server. AD CS ermöglicht Ihnen das Erstellen einer Public Key-Infrastruktur (PKI) und die Bereitstellung von Kryptografie mit öffentlichem Schlüssel, digitalen Zertifikaten und Funktionen für digitale Signaturen in Ihrer Organisation.

Wenn Sie Zertifikate für digitale Server für die Authentifizierung zwischen Computern im Netzwerk verwenden, stellen die Zertifikate Folgendes bereit:

1. Vertraulichkeit durch Verschlüsselung.

2. Integrität durch digitale Signaturen.

3. Authentifizierung durch Zuordnen von Zertifikat Schlüsseln zu Computern, Benutzern oder Geräte Konten in einem Computernetzwerk.

Weitere Informationen finden [Sie unterschritt-für-Schritt-Anleitung für AD CS: Bereitstellung](https://social.technet.microsoft.com/wiki/contents/articles/15037.ad-cs-step-by-step-guide-two-tier-pki-hierarchy-deployment.aspx)der PKI-Hierarchie mit zwei Ebenen.

## <a name="active-directory-domain-services-ad-ds"></a>Active Directory-Domänendienste (AD DS)

Mit AD DS wird eine verteilte Datenbank bereitgestellt, in der Informationen zu Netzwerkressourcen und anwendungsspezifische Daten aus AD-fähigen Anwendungen gespeichert und verwaltet werden. Administratoren können AD DS verwenden, um die Elemente eines Netzwerks (z. B. Benutzer, Computer und andere Geräte) in einer hierarchischen Struktur aus Einschlussbeziehungen zu organisieren. Diese hierarchische Struktur umfasst die Active Directory-Gesamtstruktur, Domänen in der Gesamtstruktur sowie die Organisationseinheiten in den einzelnen Domänen. Ein Server, auf dem AD DS ausgeführt wird, wird als Domänencontroller bezeichnet.

AD DS enthält die Benutzerkonten, Computer Konten und Konto Eigenschaften, die für die Authentifizierung von Benutzer Anmelde Informationen und das Auswerten der Autorisierung von VPN-Verbindungsanforderungen für das Protected Extensible Authentication-Protokoll (PAP) erforderlich sind. Weitere Informationen zum Bereitstellen von AD DS finden Sie im Windows Server 2016- [Kern Netzwerk Handbuch](../../../../networking/core-network-guide/Core-Network-Guide.md).

Während der Ausführung der Schritte in dieser Bereitstellung konfigurieren Sie die folgenden Elemente auf dem Domänen Controller.

- Aktivieren der automatischen Registrierung von Zertifikaten in Gruppenrichtlinie für Computer und Benutzer

- Erstellen der Gruppe "VPN-Benutzer"

- Erstellen der VPN-Server Gruppe

- Erstellen der NPS-Server Gruppe

### <a name="active-directory-users-and-computers"></a>Active Directory-Benutzer und-Computer

Active Directory Benutzer und Computer ist eine Komponente von AD DS, die Konten enthält, die physische Entitäten darstellen, z. b. einen Computer, eine Person oder eine Sicherheitsgruppe. Bei einer Sicherheitsgruppe handelt es sich um eine Sammlung von Benutzer-oder Computer Konten, die von Administratoren als einzelne Einheit verwaltet werden können. Benutzer-und Computer Konten, die einer bestimmten Gruppe angehören, werden als Gruppenmitglieder bezeichnet.

Benutzerkonten in Active Directory Benutzern und Computern verfügen über DFÜ-Eigenschaften, die NPS während der Autorisierung auswertet, es sei denn, die Eigenschaft **Netzwerk Zugriffsberechtigung** des Benutzerkontos ist so festgelegt, dass der **Zugriff über NPS-Netzwerk Richtlinie gesteuert wird.** . Dies ist die Standardeinstellung für alle Benutzerkonten. In einigen Fällen kann diese Einstellung jedoch eine andere Konfiguration aufweisen, die den Benutzer daran hindert, eine VPN-Verbindung herzustellen. Um diese Möglichkeit zu schützen, können Sie den NPS-Server so konfigurieren, dass Benutzerkonto-Einwähleigenschaften ignoriert werden.

Weitere Informationen finden Sie unter [Konfigurieren von NPS zum Ignorieren von Benutzerkonto-DFÜ-Eigenschaften](../../../../networking/technologies/nps/nps-np-configure.md#configure-nps-to-ignore-user-account-dial-in-properties).

### <a name="group-policy-management"></a>Gruppenrichtlinienverwaltung

Gruppenrichtlinie Management ermöglicht die Verzeichnis basierte Änderungs-und Konfigurations Verwaltung von Benutzer-und Computereinstellungen, einschließlich Sicherheits-und Benutzerinformationen. Mit Gruppenrichtlinie können Sie Konfigurationen für Gruppen von Benutzern und Computern definieren.

Mit Gruppenrichtlinie können Sie Einstellungen für Registrierungseinträge, Sicherheit, Software Installation, Skripts, Ordner Umleitung, Remoteinstallations Dienste und Internet Explorer-Wartung angeben. Die Gruppenrichtlinie Einstellungen, die Sie erstellen, sind in einem Gruppenrichtlinie Objekt (GPO) enthalten. Durch Zuordnen eines Gruppenrichtlinien Objekts zu ausgewählten Active Directory System Containern – Websites, Domänen und Organisationseinheiten – können Sie die Einstellungen des GPO auf die Benutzer und Computer in diesen Active Directory Containern anwenden. Zum Verwalten von Gruppenrichtlinie Objekten in einem Unternehmen können Sie die Gruppenrichtlinienverwaltungs-Editor Microsoft Management Console (MMC) verwenden.

## <a name="windows-10-vpn-clients"></a>Windows 10-VPN-Clients

Stellen Sie zusätzlich zu den Serverkomponenten sicher, dass auf den Client Computern, die Sie für die Verwendung von VPN konfigurieren, Windows 10 Anniversary Update (Version 1607) ausgeführt wird. Die Windows 10-VPN-Clients müssen Ihrer Active Directory Domäne beitreten.


Der Windows 10-VPN-Client ist sehr konfigurierbar und bietet viele Optionen. Um die spezifischen Features dieses Szenarios besser zu veranschaulichen, identifiziert Tabelle 1 die VPN-Funktions Kategorien und die spezifischen Konfigurationen, auf die diese Bereitstellung verweist. Sie konfigurieren die einzelnen Einstellungen für diese Features mithilfe des VPNv2-Konfigurations Dienstanbieters (CSP), der später in dieser Bereitstellung beschrieben wird. 

Tabelle 1: In dieser Bereitstellung erörterte VPN-Features und-Konfigurationen

| VPN-Feature     |     Konfiguration der Bereitstellungs Szenarien         |
|-----------------|-----------------------------------------------|
| Verbindungstyp |                 Native IKEv2                  |
|     Routing     |                Tunnelung aufteilen                |
| Namensauflösung |  Domänen Namen-Informationsliste und DNS-Suffix  |
|   Ängste    |    Erkennung von Always on und vertrauenswürdigen Netzwerken    |
| Authentifizierung  | Peer-TLS mit TPM – geschützte Benutzerzertifikate |

>[!NOTE]
>"Peer-TLS" und "TPM" sind "geschütztes Extensible Authentication Protocol with Transport Layer Security" und "Trusted Platform Module".

### <a name="vpnv2-csp-nodes"></a>VPNv2-CSP-Knoten

In dieser Bereitstellung verwenden Sie den Knoten profileXML VPNv2 CSP, um das VPN-Profil zu erstellen, das an Windows 10-Client Computer übermittelt wird. Konfigurations Dienstanbieter (CSPs) sind Schnittstellen, die verschiedene Verwaltungsfunktionen innerhalb des Windows-Clients verfügbar machen. konzeptionell funktionieren CSPs ähnlich wie Gruppenrichtlinie. Jeder CSP verfügt über Konfigurations Knoten, die einzelne Einstellungen darstellen. Ebenso wie Gruppenrichtlinie Einstellungen können Sie CSP-Einstellungen mit Registrierungs Schlüsseln, Dateien, Berechtigungen usw. verknüpfen. Ähnlich wie bei der Verwendung des Gruppenrichtlinienverwaltungs-Editor zum Konfigurieren von Gruppenrichtlinie Objekten (GPOs) konfigurieren Sie die CSP-Knoten mithilfe einer MDM-Lösung (Mobile Device Management, Verwaltung mobiler Geräte), wie z. b. Microsoft InTune. MDM-Produkte wie InTune bieten eine benutzerfreundliche Konfigurationsoption, mit der der CSP im Betriebssystem konfiguriert wird.

![Konfiguration der Verwaltung mobiler Geräte in CSP](../../../media/Always-On-Vpn/Vpn-Mdm.jpg)

Einige CSP-Knoten können jedoch nicht direkt über eine Benutzeroberfläche (UI) wie die Intune-Verwaltungskonsole konfiguriert werden. In diesen Fällen müssen Sie die Oma-URI-Einstellungen (Open Mobile Alliance Uniform Resource Identifier) manuell konfigurieren. Sie konfigurieren Oma-URIs mithilfe des Oma-Geräte Verwaltungs Protokolls (OMA-DM), einer universellen Geräte Verwaltungs Spezifikation, die von den meisten modernen Apple-, Android-und Windows-Geräten unterstützt wird. Solange Sie der OMA-DM-Spezifikation entsprechen, sollten alle MDM-Produkte auf die gleiche Weise mit diesen Betriebssystemen interagieren.

Windows 10 bietet viele CSPs, aber bei dieser Bereitstellung liegt der Schwerpunkt auf der Verwendung von VPNv2 CSP zum Konfigurieren des VPN-Clients. Der VPNv2 CSP ermöglicht die Konfiguration der einzelnen VPN-Profileinstellungen in Windows 10 über einen eindeutigen CSP-Knoten. Außerdem ist der VPNv2-CSP ein Knoten namens *profileXML*, der es Ihnen ermöglicht, alle Einstellungen in einem Knoten anstatt einzeln zu konfigurieren. Weitere Informationen zu profileXML finden Sie im Abschnitt "Übersicht über profileXML" weiter unten in dieser Bereitstellung. Ausführliche Informationen zu den einzelnen VPNv2-CSP-Knoten finden Sie unter [VPNv2 CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/vpnv2-csp).

## <a name="next-steps"></a>Nächste Schritte

- [Erfahren Sie mehr über die erweiterten Always on-VPN-Features](deploy/always-on-vpn-adv-options.md)

- [Beginnen der Planung Ihrer Always on-VPN-Bereitstellung](deploy/always-on-vpn-deploy-deployment.md)

## <a name="related-topics"></a>Verwandte Themen

- [Microsoft-Server Softwareunterstützung für Microsoft Azure Virtual Machines](https://support.microsoft.com/help/2721672/microsoft-server-software-support-for-microsoft-azure-virtual-machines): In diesem Artikel wird die Unterstützungs Richtlinie für die Ausführung von Microsoft-Server Software in der Microsoft Azure virtuellen Computerumgebung (Infrastructure-as-a-Service) erläutert.

- [Remote Zugriff](../../Remote-Access.md): Dieses Thema enthält eine Übersicht über die Remote Zugriffs-Server Rolle in Windows Server 2016.

- [Technische Anleitung für Windows 10-VPN](https://docs.microsoft.com/windows/access-protection/vpn/vpn-guide): Dieser Leitfaden führt Sie durch die Entscheidungen, die Sie für Windows 10-Clients in Ihrer Enterprise-VPN-Lösung treffen werden, und wie Sie Ihre Bereitstellung konfigurieren. Dieses Handbuch verweist auf den VPNv2-Konfigurations Dienstanbieter (CSP) und stellt Konfigurations Anweisungen für die Verwaltung mobiler Geräte (MDM) mithilfe von Microsoft InTune und der VPN-Profil Vorlage für Windows 10 bereit.

- [Handbuch](../../../../networking/core-network-guide/Core-Network-Guide.md)zum Hauptnetzwerk: Dieses Handbuch enthält Anweisungen zum Planen und Bereitstellen der Kernkomponenten, die für ein voll funktionsfähiges Netzwerk und eine neue Active Directory Domäne in einer neuen Gesamtstruktur erforderlich sind.

- [Domain Name System (DNS)](../../../../networking/dns/dns-top.md): Dieses Thema bietet einen Überblick über Domain Name Systems (DNS). In Windows Server 2016 ist DNS eine Server Rolle, die Sie mithilfe von Server-Manager oder Windows PowerShell-Befehlen installieren können. Wenn Sie eine neue Active Directory Gesamtstruktur und Domäne installieren, wird DNS automatisch mit Active Directory als globaler Katalogserver für die Gesamtstruktur und Domäne installiert.

- [Übersicht über Active Directory Zertifikat Dienste](https://technet.microsoft.com/library/hh831740.aspx): Dieses Dokument bietet einen Überblick über die Active Directory Zertifikat Dienste (AD CS) in Windows Server® 2012. AD CS ist die Serverrolle, die es Ihnen ermöglicht, eine Public Key Infrastructure (PKI) zu erstellen und Verschlüsselung für öffentliche Schlüssel, digitale Zertifikate und Funktionen für digitale Signaturen in Ihrer Organisation bereitzustellen.

- [Entwurfs Leit Faden für die Public Key-Infrastruktur](https://social.technet.microsoft.com/wiki/contents/articles/2901.public-key-infrastructure-design-guidance.aspx):  Dieses wiki bietet Anleitungen zum Entwerfen von Public Key Infrastructure (PKIs). Bevor Sie eine PKI-und Zertifizierungsstellen Hierarchie konfigurieren, sollten Sie die Sicherheitsrichtlinie und die CPS-Anweisung (Certificate Practice Statement) Ihrer Organisation kennen.

- [Schritt-für-Schritt-Anleitung für AD CS: Bereitstellung](https://social.technet.microsoft.com/wiki/contents/articles/15037.ad-cs-step-by-step-guide-two-tier-pki-hierarchy-deployment.aspx)der PKI-Hierarchie mit zwei Ebenen: Diese Schritt-für-Schritt-Anleitung beschreibt die Schritte, die erforderlich sind, um eine grundlegende Konfiguration von Active Directory® Zertifikat Diensten (AD CS) in einer Lab-Umgebung einzurichten. AD CS in Windows Server® 2008 R2 bietet anpassbare Dienste zum Erstellen und Verwalten von Zertifikaten für öffentliche Schlüssel, die in Software Sicherheitssystemen verwendet werden, die Public Key-Technologien einsetzen.

- [Netzwerk Richtlinien Server (Network Policy Server, NPS)](../../../../networking/technologies/nps/nps-top.md): Dieses Thema enthält eine Übersicht über den Netzwerk Richtlinien Server in Windows Server 2016. Mit einem Netzwerkrichtlinienserver (Network Policy Server, NPS) können Sie organisationsweite Netzwerkzugriffsrichtlinien für die Authentifizierung und Autorisierung von Verbindungsanforderungen erstellen und erzwingen.
