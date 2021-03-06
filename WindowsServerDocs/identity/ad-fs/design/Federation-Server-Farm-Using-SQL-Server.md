---
ms.assetid: e983d2ab-4153-41e7-b243-12cf7d71a552
title: Verbundserverfarm mit SQL Server
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 0ab150a5070f076db70941bb106b42c3fb15411e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408098"
---
# <a name="federation-server-farm-using-sql-server"></a>Verbundserverfarm mit SQL Server

Diese Topologie für Active Directory-Verbunddienste (AD FS) \(AD FS\) unterscheidet sich von der Verbund Serverfarm mithilfe der \(internen\) Windows-Datenbank-wid-Bereitstellungs Topologie darin, dass die Daten nicht in repliziert werden. Alle Verbund Server in der Farm. Stattdessen können alle Verbund Server in der Farm Daten in eine gemeinsame Datenbank lesen und schreiben, die auf einem Server mit Microsoft SQL Server gespeichert ist, der sich im Unternehmensnetzwerk befindet.  
  
> [!IMPORTANT]  
> Wenn Sie eine AD FS-Farm erstellen und Ihre Konfigurationsdaten mit SQL Server speichern möchten, können Sie SQL Server 2008 und neuere Versionen verwenden, einschließlich SQL Server 2012 und SQL Server 2014.  
  
## <a name="deployment-considerations"></a>Überlegungen zur Bereitstellung  
In diesem Abschnitt werden verschiedene Überlegungen zu den beabsichtigten Zielgruppen, Vorteilen und Einschränkungen beschrieben, die mit dieser Bereitstellungs Topologie verknüpft sind.  
  
### <a name="who-should-use-this-topology"></a>Wer sollte diese Topologie verwenden?  
  
-   Große Unternehmen mit mehr als 100 Vertrauens Stellungen, die sowohl internen als auch externen Benutzern\- \(SSO\) -Zugriff auf Verbund Anwendungen oder-Dienste bereitstellen müssen  
  
-   Organisationen, die bereits SQL Server verwenden und Ihre vorhandenen Tools und Fachkenntnisse nutzen möchten  
  
### <a name="what-are-the-benefits-of-using-this-topology"></a>Welche Vorteile bietet die Verwendung dieser Topologie?  
  
-   Unterstützung für \(eine größere Anzahl von Vertrauens Stellungen mehr als 100\)  
  
-   Unterstützung für die Erkennung \(von tokenwiedergabe, eine \(Sicherheitsfunktion\) und einen \(artefaktauflösungs Teil des Security Assertion Markup Language SAML\) 2,0-Protokolls\)  
  
-   Unterstützung für die vollständigen Vorteile von SQL Server, z. b. Daten Bank Spiegelung, Failoverclustering, Berichterstellung und Verwaltungs Tools  
  
### <a name="what-are-the-limitations-of-using-this-topology"></a>Welche Einschränkungen gelten für die Verwendung dieser Topologie?  
  
-   Diese Topologie bietet standardmäßig keine Daten Bank Redundanz. Obwohl eine Verbund Serverfarm mit wid-Topologie die wid-Datenbank automatisch auf jedem Verbund Server in der Farm repliziert, enthält die Verbund Serverfarm mit SQL Server Topologie nur eine Kopie der Datenbank.  
  
> [!NOTE]  
> SQL Server unterstützt viele verschiedene Daten-und Anwendungs Redundanz Optionen, einschließlich Failoverclustering, Daten Bank Spiegelung und verschiedene Typen von SQL Server Replikation.  
  
Die \(IT\- \-\) \(-Abteilung der Microsoft Information Technology verwendet SQL Server Daten Bank Spiegelung im synchronen Modus mit hoher Sicherheit und Failoverclustering für hohe\) Verfügbarkeits Unterstützung für die SQL Server-Instanz. SQL Server transaktionaler \(Peer\--\-to\) -Peer-und Mergereplikation wurde nicht vom AD FS-Produktteam bei Microsoft getestet. Weitere Informationen zu SQL Server finden Sie unter [Übersicht über Lösungen mit hoher Verfügbarkeit](https://go.microsoft.com/fwlink/?LinkId=179853) oder [auswählen des geeigneten Replikations Typs](https://go.microsoft.com/fwlink/?LinkId=214648).  
  
### <a name="supported-sql-server-versions"></a>Unterstützte SQL Server Versionen  
Die folgenden SQL Server-Versionen werden mit AD FS in Windows Server 2012 R2 unterstützt:  
  
-   SQL Server 2008 \/ R2  
  
-   SQL Server 2012  
  
-   SQL Server 2014  
  
## <a name="server-placement-and-network-layout-recommendations"></a>Empfehlungen zur Server Platzierung und zum Netzwerk Layout  
Ähnlich der Verbund Serverfarm mit der wid-Topologie sind alle Verbund Server in der Farm so konfiguriert, dass Sie einen Cluster Domain Name System \(DNS\) - \(Namen verwenden, der den Verbunddienst Namen\)darstellt.und eine Cluster-IP-Adresse als Teil der NLB \(\) -Cluster Konfiguration für den Netzwerk Lastenausgleich. Dadurch kann der NLB-Host Client Anforderungen den einzelnen Verbund Servern zuordnen. Verbund Server Proxys können zum Proxy von Client Anforderungen an die Verbund Serverfarm verwendet werden.  
  
In der folgenden Abbildung wird gezeigt, wie das fiktive Unternehmen von Unternehmen in der Verbund Serverfarm mit SQL Server Topologie im Unternehmensnetzwerk bereitgestellt hat. Außerdem wird gezeigt, wie das Unternehmen das Umkreis Netzwerk mit Zugriff auf einen DNS-Server konfiguriert hat, einem zusätzlichen NLB-Host, der \(denselben\) DNS-Cluster Namen verwendet FS.contoso.com, der im NLB-Cluster des Unternehmensnetzwerks verwendet wird, und mit zwei Web- Anwendungs Proxys \(wap1\)und WAP2.  
  
![Serverfarm mit SQL](media/SQLFarmADFSBlue.gif)  
  
Weitere Informationen zum Konfigurieren der Netzwerkumgebung für die Verwendung mit Verbund Servern oder webanwendungsproxys finden Sie im Abschnitt "Anforderungen für die Namensauflösung" unter [AD FS Anforderungen](AD-FS-Requirements.md) und [Planen der Infrastruktur für den webanwendungsproxy. (WAP)](https://technet.microsoft.com/library/dn383648.aspx).  
  
## <a name="high-availability-options-for-sql-server-farms"></a>Optionen für hohe Verfügbarkeit für SQL Server Farmen  
In Windows Server 2012 R2 gibt es AD FS zwei neue Optionen zur Unterstützung der Hochverfügbarkeit in AD FS Farmen mit SQL Server.  
  
-   Unterstützung für SQL Server AlwaysOn-Verfügbarkeitsgruppen  
  
-   Unterstützung für geografisch verteilte Hochverfügbarkeit mithilfe SQL Server Mergereplikation  
  
In diesem Abschnitt werden die einzelnen Optionen, die von Ihnen auftretenden Probleme und einige wichtige Aspekte bei der Entscheidung beschrieben, welche Optionen bereitgestellt werden müssen.  
  
> [!NOTE]  
> AD FS Farmen, die die interne Windows \(-\) Datenbank wid verwenden, stellen Grund\/Legende Datenredundanz mit Lesezugriff\-auf den primären Verbund Server Knoten und schreibgeschützten Zugriff auf sekundären Knoten bereit.  Dies kann in einer geografisch lokalen oder geografisch verteilten Topologie verwendet werden.  
>   
> Beachten Sie bei der Verwendung von wid die folgenden Einschränkungen:  
>   
> -   Eine wid-Farm hat ein Limit von 30 Verbund Servern, wenn Sie über 100 oder weniger Vertrauens Stellungen der vertrauenden Seite verfügen.  
> -   Eine wid-Farm unterstützt keine tokenwiedergabe-oder \(artefaktauflösungs Teile \(des Security Assertion Markup Language\) SAML-Protokolls\).  
  
In der folgenden Tabelle finden Sie eine Zusammenfassung zur Verwendung einer wid-Farm.  
  
||||  
|-|-|-|  
||1 \- 100 RP-Vertrauens Stellungen|Mehr als 100 RP-Vertrauens Stellungen|  
|1 \- 30 AD FS Knoten|Unterstützt wid|Nicht unterstützt, \- wenn wid SQL erforderlich ist|  
|Mehr als 30 AD FS Knoten|Nicht unterstützt, \- wenn wid SQL erforderlich ist|Nicht unterstützt, \- wenn wid SQL erforderlich ist|  
  
### <a name="alwayson-availability-groups"></a>AlwaysOn-Verfügbarkeitsgruppen  
**Übersicht**  
  
AlwaysOn-Verfügbarkeits Gruppen wurden in SQL Server 2012 eingeführt und bieten eine neue Möglichkeit zum Erstellen einer hoch Verfügbarkeits SQL Server Instanz.  AlwaysOn-Verfügbarkeits Gruppen kombinieren Elemente von Clustering und Daten Bank Spiegelung für Redundanz und Failover auf der SQL-Instanzebene und der Datenbankebene.  Im Gegensatz zu vorherigen hoch Verfügbarkeits Optionen benötigen AlwaysOn-Verfügbarkeits Gruppen keinen \(allgemeinen Speicher\) oder Storage Area Network auf Datenbankebene.  
  
Eine \(Verfügbarkeits Gruppe besteht aus einem primären Replikat, einem Satz von primären Datenbanken\) mit Lese\--/Schreibzugriff und einem\)bis vier Verfügbarkeits Replikat \(Sätzen entsprechender Sekund  Die Verfügbarkeits Gruppe\-unterstützt \(das primäre Replikat\)mit Lese-/Schreibzugriff\-und ein bis vier schreibgeschützte Verfügbarkeits Replikate.  Jedes Verfügbarkeits Replikat muss sich in einem anderen Knoten eines einzelnen wsfc \(\) -Clusters mit Windows Server-Failoverclustering befinden.  Weitere Informationen zu AlwaysOn-Verfügbarkeits Gruppen finden Sie unter [Übersicht\)über AlwaysOn-Verfügbarkeitsgruppen \(SQL Server](https://technet.microsoft.com/library/ff877884.aspx).  
  
Aus Sicht der Knoten einer AD FS SQL Server Farm ersetzt die AlwaysOn-Verfügbarkeits Gruppe die einzelne SQL Server Instanz als die Richtlinien \/ artefaktdatenbank.  Der verfügbarkeitsgruppenlistener gibt den \(Client an, den der\) AD FS Sicherheitstokendienst zum Herstellen einer Verbindung mit SQL verwendet.  
  
Das folgende Diagramm zeigt eine AD FS SQL Server Farm mit AlwaysOn-Verfügbarkeits Gruppe.  
  
![Serverfarm mit SQL](media/alwaysonavailabilitygroups.jpg)  
  
> [!NOTE]  
> AlwaysOn-Verfügbarkeits Gruppen erfordern, dass sich die SQL Server Instanzen auf wsfc \(\) -Knoten des Windows Server-Failoverclustering befinden.  
  
> [!NOTE]  
> Nur ein Verfügbarkeits Replikat kann als automatisches failoverziel fungieren, die anderen drei basieren auf manuellen Failover.  
  
**Wichtige Aspekte der Bereitstellung**  
  
Wenn Sie die Verwendung von AlwaysOn-Verfügbarkeits Gruppen in Kombination mit SQL Server Mergereplikation planen, notieren Sie sich die unter "wichtige Überlegungen zur Bereitstellung bei der Verwendung AD FS mit SQL Server Mergereplikation" beschriebenen Probleme.  Insbesondere wenn eine AlwaysOn-Verfügbarkeits Gruppe, die eine Datenbank enthält, die ein Replikations Abonnent ist, ein Failover des Replikations Abonnements durchführt. Zum Fortsetzen der Replikation muss der Abonnent von einem Replikations Administrator manuell neu konfiguriert werden.  Weitere Informationen finden Sie unter SQL Server Beschreibung eines bestimmten Problems bei [Replikations Abonnenten \(und AlwaysOn-Verfügbarkeitsgruppen SQL Server\) ](https://technet.microsoft.com/library/hh882436.aspx) und allgemeine Unterstützungs Anweisungen für AlwaysOn-Verfügbarkeits Gruppen mit Replikations Optionen unter [ Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen \(SQL Server\)](https://technet.microsoft.com/library/hh403414.aspx).  
  
**Konfigurieren von AD FS für die Verwendung einer AlwaysOn-Verfügbarkeits Gruppe**  
  
Das Konfigurieren einer AD FS-Farm mit AlwaysOn-Verfügbarkeits Gruppen erfordert eine geringfügige Änderung des AD FS Bereitstellungs Verfahrens:  
  
1.  Die Datenbanken, die Sie sichern möchten, müssen erstellt werden, bevor die AlwaysOn-Verfügbarkeits Gruppen konfiguriert werden können.  AD FS erstellt seine Datenbanken im Rahmen der Einrichtung und Erstkonfiguration des ersten Verbund Dienst Knotens einer neuen AD FS SQL Server Farm.  Als Teil der AD FS Konfiguration müssen Sie eine SQL-Verbindungs Zeichenfolge angeben. Daher müssen Sie den ersten AD FS Farm Knoten so konfigurieren, dass eine direkte \(Verbindung mit einer SQL-Instanz hergestellt wird. Dies ist nur vorübergehend.\)   Spezifische Anleitungen zum Konfigurieren einer AD FS-Farm, einschließlich der Konfiguration eines AD FS Farm Knotens mit einer SQL Server-Verbindungs Zeichenfolge, finden Sie unter [Konfigurieren eines Verbund Servers](../../ad-fs/deployment/Configure-a-Federation-Server.md).  
  
2.  Nachdem die AD FS Datenbanken erstellt wurden, weisen Sie Sie AlwaysOn-Verfügbarkeits Gruppen zu, und erstellen Sie den allgemeinen tcpip-Listener mithilfe SQL Server Tools und Prozesses bei [der \(Erstellung\) und Konfiguration von Verfügbarkeits Gruppen SQL Server ](https://technet.microsoft.com/library/ff878265.aspx).  
  
3.  Verwenden Sie abschließend PowerShell zum Bearbeiten der AD FS Eigenschaften, um die SQL-Verbindungs Zeichenfolge so zu aktualisieren, dass Sie die DNS-Adresse des Listener der AlwaysOn-Verfügbarkeits Gruppe verwendet.  
  
    Beispiel-PSH-Befehle zum Aktualisieren der SQL-Verbindungs Zeichenfolge für die AD FS Konfigurations Datenbank:  
  
    ```  
    PS:\>$temp= Get-WmiObject -namespace root/ADFS -class SecurityTokenService  
    PS:\>$temp.ConfigurationdatabaseConnectionstring=”data source=<SQLCluster\SQLInstance>; initial catalog=adfsconfiguration;integrated security=true”  
    PS:\>$temp.put()  
  
    ```  
  
4.  Beispiel-PSH-Befehle zum Aktualisieren der SQL-Verbindungs Zeichenfolge für die AD FS artefaktauflösungs-Dienst Datenbank:  
  
    ```  
    PS:\> Set-AdfsProperties –artifactdbconnection ”Data source=<SQLCluster\SQLInstance >;Initial Catalog=AdfsArtifactStore;Integrated Security=True”  
    ```  
  
### <a name="sql-server-merge-replication"></a>SQL Server Mergereplikation  
Die Mergereplikation wird auch in SQL Server 2012 eingeführt und ermöglicht die Redundanz von AD FS Richtlinien Daten mit den folgenden Merkmalen:  
  
-   Lese-und Schreibfunktion auf allen \(Knoten, nicht nur auf dem primären\)  
  
-   Kleinere Datenmengen, die asynchron repliziert werden, um eine Einführung in das System zu vermeiden  
  
Das folgende Diagramm zeigt eine geografisch redundante AD FS SQL Server Farmen mit Mergereplikation \(1 Publisher, 2 Abonnenten:\)  
  
![Serverfarm mit SQL](media/ADFSSQLGeoRedundancy3.png)  
  
**Wichtige Überlegungen zur Bereitstellung bei der Verwendung von \(AD FS mit SQL Server mergereplikationsnotieren im obigen Diagramm\)**  
  
-   Die Verteiler Datenbank wird für die Verwendung mit AlwaysOn-Verfügbarkeitsgruppen oder Daten Bank Spiegelung nicht unterstützt.  Weitere Informationen finden Sie unter SQL Server Support-Anweisungen für AlwaysOn-Verfügbarkeits Gruppen mit Replikations Optionen bei [Replikation\), Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen \(SQL Server](https://technet.microsoft.com/library/hh403414.aspx).  
  
-   Wenn eine AlwaysOn-Verfügbarkeits Gruppe, die eine Datenbank enthält, bei der es sich um einen Replikations Abonnenten handelt, ein Failover durchführt Zum Fortsetzen der Replikation muss der Abonnent von einem Replikations Administrator manuell neu konfiguriert werden.  Weitere Informationen finden Sie unter SQL Server Beschreibung eines bestimmten Problems bei [Replikations Abonnenten \(und AlwaysOn-Verfügbarkeitsgruppen SQL Server\) ](https://technet.microsoft.com/library/hh882436.aspx) und allgemeine Unterstützungs Anweisungen für AlwaysOn-Verfügbarkeits Gruppen mit Replikations Optionen [ Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen \(SQL Server\)](https://technet.microsoft.com/library/hh403414.aspx).  
  
Ausführlichere Anweisungen zum Konfigurieren von AD FS für die Verwendung einer SQL Server Mergereplikation finden Sie unter [Einrichten der geografischen Redundanz mit SQL Server-Replikation](https://technet.microsoft.com/library/dn632406.aspx).  
  
## <a name="see-also"></a>Siehe auch  
[Planen der AD FS-Bereitstellungstopologie](Plan-Your-AD-FS-Deployment-Topology.md)  
[AD FS-Entwurfshandbuch in Windows Server 2012 R2](AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)  
  

