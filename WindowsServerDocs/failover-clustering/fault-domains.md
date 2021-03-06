---
ms.assetid: 56fc7f80-9558-467e-a6e9-a04c9abbee33
title: Fehlerdomänenunterstützung
ms.prod: windows-server
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-failover-clustering
ms.topic: article
author: cosmosdarwin
ms.date: 09/16/2016
ms.openlocfilehash: 439f898b7c96ecc3d2f380509fe86d528aa737c5
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71361142"
---
# <a name="fault-domain-awareness"></a>Fehlerdomänenunterstützung

> Gilt für: Windows Server 2019 und Windows Server 2016

Failoverclustering ermöglicht die Zusammenarbeit mehrerer Server, um hohe Verfügbarkeit zu bieten – oder anders ausgedrückt, um Knotenfehlertoleranz zu bieten. Die heutigen Unternehmen verlangen jedoch eine immer höhere Verfügbarkeit Ihrer Infrastruktur. Um cloudähnliche Betriebszeit zu erreichen, ist auch der Schutz bei sehr unwahrscheinlichen Vorfällen wie z.B. Gehäuse- und Rackausfällen oder Naturkatastrophen erforderlich. Aus diesem Grund haben Failoverclustering in Windows Server 2016 auch Gehäuse-, Rack-und Site Fehlertoleranz eingeführt.

## <a name="fault-domain-awareness"></a>Fehlerdomänenunterstützung

Fehlerdomänen und Fehlertoleranz sind eng miteinander verwandte Konzepte. Eine Fehlerdomäne ist eine Reihe von Hardwarekomponenten, die einen gemeinsamen Single Point of Failure haben. Um ein bestimmtes Niveau an Fehlertoleranz zu erzielen, benötigen Sie mehrere Fehlerdomänen auf dieser Ebene. Beispielsweise setzt Rackfehlertoleranz voraus, dass Ihre Server und Daten auf mehrere Racks verteilt sind.

Dieses kurze Video bietet eine Übersicht über Fehler Domänen in Windows Server 2016:  
[![ Klicken Sie auf dieses Bild, um eine Übersicht über Fehler Domänen in Windows Server 2016 anzuzeigen.](media/Fault-Domains-in-Windows-Server-2016/Part-1-Fault-Domains-Overview.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-1-Overview)

### <a name="fault-domain-awareness-in-windows-server-2019"></a>Fehler Domänen Bewusstsein in Windows Server 2019

Fehler Domänen Bewusstsein ist in Windows Server 2019 verfügbar, aber standardmäßig deaktiviert und muss über die Windows-Registrierung aktiviert werden.

Um das Fehler Domänen Bewusstsein in Windows Server 2019 zu aktivieren, wechseln Sie zur Windows-Registrierung, und legen Sie (Get-Cluster) fest. Autozuzustandsite-Registrierungsschlüssel auf 1.

```Registry
    (Get-Cluster).AutoAssignNodeSite=1
```

Um das Fehler Domänen Bewusstsein in Windows 2019 zu deaktivieren, navigieren Sie zur Windows-Registrierung, und legen Sie (Get-Cluster) fest. Autozuzustandsite-Registrierungsschlüssel auf 0 (null).

```Registry
    (Get-Cluster).AutoAssignNodeSite=0
```

## <a name="benefits"></a>Vorteile
- **Speicherplätze, einschließlich direkte Speicherplätze, verwenden Fehler Domänen, um die Datensicherheit zu maximieren.**  
    Die Resilienz in „Speicherplätze“ ist konzeptionell wie verteiltes, softwaredefiniertes RAID. Mehrere Kopien aller Daten werden synchron beibehalten, und wenn bei einem Hardwareausfall eine Kopie verloren geht, werden andere zum Wiederherstellen der Resilienz erneut kopiert. Um die bestmögliche Resilienz zu erreichen, sollten Kopien in separaten Fehlerdomänen beibehalten werden.

- **Der [Integritätsdienst](health-service-overview.md) verwendet Fehler Domänen, um hilfreichere Warnungen bereitzustellen.**  
    Jeder Fehlerdomäne können Speicherortmetadaten zugeordnet werden, die automatisch in alle nachfolgenden Warnungen aufgenommen werden. Diese Deskriptoren können Vorgänge oder Wartungspersonal unterstützen und Fehler reduzieren, indem sie Hardware eindeutig machen.  

- **Stretch Clustering verwendet Fehler Domänen für die Speicher Affinität.** Stretch-Clustering ermöglicht weit entfernten Servern, einem gemeinsamen Cluster beitreten. Für optimale Leistung sollten Anwendungen oder virtuelle Computer auf Servern ausgeführt werden, die sich in der Nähe derer befinden, die ihnen Speicherplatz bereitstellen. Fehler Domänen Bewusstsein ermöglicht diese Speicher Affinität.   

## <a name="levels-of-fault-domains"></a>Ebenen der Fehlerdomänen  
Es gibt vier kanonische Ebenen von Fehlerdomänen – Standort, Rack, Gehäuse und Knoten. Knoten werden automatisch erkannt; jede zusätzliche Ebene ist optional. Wenn Ihre Bereitstellung beispielsweise keine Blade Server enthält, ist die Gehäuseebene für Sie wahrscheinlich nicht sinnvoll.  

![Diagramm der verschiedenen Ebenen von Fehler Domänen](media/Fault-Domains-in-Windows-Server-2016/levels-of-fault-domains.png)

## <a name="usage"></a>Verwendung  
Sie können PowerShell oder XML-Markup zum Angeben von Fehler Domänen verwenden. Beide Ansätze sind äquivalent und bieten vollständige Funktionalität.

>[!IMPORTANT]
> Geben Sie Fehlerdomänen wenn möglich an, bevor Sie „Direkte Speicherplätze“ aktivieren. Dies ermöglicht die Vorbereitung von Pool, Ebenen und Einstellungen wie Resilienz und Anzahl der Spalten für Gehäuse- oder Rackfehlertoleranz durch automatische Konfiguration. Wenn Pool und Volumes erstellt sind, werden Daten nicht nachträglich in Reaktion auf Änderungen der Fehlerdomänentopologie verschoben. Um nach dem Aktivieren von „Direkte Speicherplätze“ Knoten zwischen Gehäusen oder Racks zu verschieben, sollten Sie zuerst den Knoten sowie seine Laufwerke mit `Remove-ClusterNode -CleanUpDisks` aus dem Pool entfernen.

### <a name="defining-fault-domains-with-powershell"></a>Definieren von Fehler Domänen mit PowerShell
Windows Server 2016 führt die folgenden Cmdlets ein, um mit Fehler Domänen zu arbeiten:
* `Get-ClusterFaultDomain`
* `Set-ClusterFaultDomain`
* `New-ClusterFaultDomain` 
* `Remove-ClusterFaultDomain`

Dieses kurze Video veranschaulicht die Verwendung dieser Cmdlets.
[![ Klicken Sie auf dieses Bild, um sich ein kurzes Video zur Verwendung der Cluster Fehler-Domänen-Cmdlets anzusehen.](media/Fault-Domains-in-Windows-Server-2016/Part-2-Using-PowerShell.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-2-Using-PowerShell)

Verwenden Sie `Get-ClusterFaultDomain`, um die aktuelle Fehler Domänen Topologie anzuzeigen. Dadurch werden alle Knoten im Cluster sowie alle Gehäuse, Racks oder Standorte aufgelistet, die Sie erstellt haben. Sie können mit Parametern wie **-Type** oder **-Name** filtern, aber diese sind nicht erforderlich.

```PowerShell
Get-ClusterFaultDomain
Get-ClusterFaultDomain -Type Rack
Get-ClusterFaultDomain -Name "server01.contoso.com"
```

Verwenden Sie `New-ClusterFaultDomain`, um neue Chassis, Racks oder Standorte zu erstellen. Die Parameter "`-Type`" und "`-Name`" sind erforderlich. Die möglichen Werte für `-Type` sind `Chassis`, `Rack` und `Site`. Der `-Name` kann eine beliebige Zeichenfolge sein. (Bei `Node`-Typfehler Domänen muss der Name der tatsächliche Knoten Name sein, wie er automatisch festgelegt wird.)

```PowerShell
New-ClusterFaultDomain -Type Chassis -Name "Chassis 007"
New-ClusterFaultDomain -Type Rack -Name "Rack A"
New-ClusterFaultDomain -Type Site -Name "Shanghai"
```

> [!IMPORTANT]  
> Windows Server kann nicht sicherstellen, dass Fehler Domänen, die Sie erstellen, in der realen, physischen Welt übereinstimmen. (Dies mag offensichtlich klingen, aber es ist wichtig zu verstehen.) Wenn sich in der realen Welt alle Ihre Knoten in einem einzigen Rack befinden, dann schafft das Erstellen von zwei `-Type Rack`-Fehlerdomänen in der Software nicht auf magische Weise Rackfehlertoleranz. Sie sind dafür verantwortlich, sicherzustellen, dass die Topologie, die Sie mithilfe dieser Cmdlets erstellen, der tatsächlichen Anordnung der Hardware entspricht.

Verwenden Sie `Set-ClusterFaultDomain`, um eine Fehler Domäne in eine andere zu verschieben. Die Begriffe „übergeordnet“ und „untergeordnet“ werden häufig zur Beschreibung dieser geschachtelten Beziehung verwendet. Die Parameter "`-Name`" und "`-Parent`" sind erforderlich. Geben Sie in `-Name` den Namen der Fehler Domäne an, die verschoben wird. Geben Sie in `-Parent` den Namen des Ziels an. Um mehrere Fehlerdomänen gleichzeitig zu verschieben, listen Sie ihre Namen auf.

```PowerShell
Set-ClusterFaultDomain -Name "server01.contoso.com" -Parent "Rack A"
Set-ClusterFaultDomain -Name "Rack A", "Rack B", "Rack C", "Rack D" -Parent "Shanghai"
```

> [!IMPORTANT]  
> Bei der Verschiebung von Fehlerdomänen werden ihre untergeordneten Objekte mit ihnen verschoben. Wenn Rack A im obigen Beispiel server01.contoso.com übergeordnet ist, muss letztere nicht separat an den Standort Shanghai verschoben werden – sie ist schon durch das übergeordnete Element dort, wie in der realen Welt.

Sie können Beziehungen zwischen übergeordneten und untergeordneten Elementen in der Ausgabe von `Get-ClusterFaultDomain` in den Spalten `ParentName` und `ChildrenNames` sehen.

Sie können auch `Set-ClusterFaultDomain` verwenden, um bestimmte andere Eigenschaften von Fehler Domänen zu ändern. Beispielsweise können Sie optionale `-Location`-oder `-Description`-Metadaten für jede Fehler Domäne bereitstellen. Wenn angegeben, werden diese Informationen in Hardwarewarnungen des Integritätsdiensts einbezogen. Sie können Fehler Domänen auch mithilfe des Parameters `-NewName` umbenennen. Benennen Sie `Node`-typfehlerdomänen nicht um.

```PowerShell
Set-ClusterFaultDomain -Name "Rack A" -Location "Building 34, Room 4010"
Set-ClusterFaultDomain -Type Node -Description "Contoso XYZ Server"
Set-ClusterFaultDomain -Name "Shanghai" -NewName "China Region"
```

Verwenden Sie `Remove-ClusterFaultDomain` zum Entfernen von Chassis, Racks oder Websites, die Sie erstellt haben. Der `-Name` -Parameter ist erforderlich. Eine Fehler Domäne, die untergeordnete Elemente enthält, kann nicht entfernt werden – entfernen Sie zunächst die untergeordneten Elemente, oder verschieben Sie Sie außerhalb der `Set-ClusterFaultDomain`. Legen Sie den `-Parent` auf die leere Zeichenfolge ("") fest, um eine Fehler Domäne außerhalb aller anderen Fehler Domänen zu verschieben. Fehler Domänen vom Typ "`Node`" können nicht entfernt werden. Um mehrere Fehlerdomänen gleichzeitig zu entfernen, listen Sie ihre Namen auf.

```PowerShell
Set-ClusterFaultDomain -Name "server01.contoso.com" -Parent ""
Remove-ClusterFaultDomain -Name "Rack A"
```

### <a name="defining-fault-domains-with-xml-markup"></a>Definieren von Fehlerdomänen mit XML-Markup
Fehlerdomänen können mithilfe einer XML-Syntax angegeben werden. Sie sollten Ihren bevorzugten Texteditor verwenden, z.B. Visual Studio Code ( *[hier](https://code.visualstudio.com/)* kostenlos erhältlich) oder Editor, um ein XML-Dokument zu erstellen, das Sie speichern und wiederverwenden können.  

Dieses kurze Video veranschaulicht die Verwendung von XML-Markup zur Angabe von Fehlerdomänen.

[![ Klicken Sie auf dieses Bild, um sich ein kurzes Video zur Verwendung von XML zum Angeben von Fehler Domänen anzusehen.](media/Fault-Domains-in-Windows-Server-2016/Part-3-Using-XML-Markup.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-3-Using-XML)

Führen Sie in PowerShell das folgende Cmdlet aus: `Get-ClusterFaultDomainXML`. Dadurch wird die aktuelle Fehlerdomänenspezifikation für den Cluster im XML-Format zurückgegeben. Dies spiegelt alle ermittelten `<Node>` wider, die beim Öffnen und Schließen von `<Topology>`-Tags umschlossen sind.  

Führen Sie Folgendes aus, um diese Ausgabe in einer Datei zu speichern.  

```PowerShell
Get-ClusterFaultDomainXML | Out-File <Path>  
```

Öffnen Sie die Datei, und fügen Sie `<Site>`-, `<Rack>`-und `<Chassis>`-Tags hinzu, um anzugeben, wie diese Knoten Zwischenstand Orten, Racks und Chassis verteilt werden. Jedes Tag muss durch einen eindeutigen **Name** identifiziert werden. Für Knoten müssen Sie den Knotennamen als standardmäßig aufgefüllt beibehalten.  

> [!IMPORTANT]  
> Während alle zusätzlichen Tags optional sind, muss die transitive Hierarchie Standort &gt; Rack &gt; Gehäuse &gt; Knoten beibehalten und ordnungsgemäß geschlossen werden.  
Zusätzlich zu Name können einem beliebigen Tag Freihand-`Location="..."`-und `Description="..."`-Deskriptoren hinzugefügt werden.  

#### <a name="example-two-sites-one-rack-each"></a>Beispiel: Zwei Standorte, jeweils ein Gestell  

```XML
<Topology>  
  <Site Name="SEA" Location="Contoso HQ, 123 Example St, Room 4010, Seattle">  
    <Rack Name="A01" Location="Aisle A, Rack 01">  
      <Node Name="Server01" Location="Rack Unit 33" />  
      <Node Name="Server02" Location="Rack Unit 35" />  
      <Node Name="Server03" Location="Rack Unit 37" />  
    </Rack>  
  </Site>  
  <Site Name="NYC" Location="Regional Datacenter, 456 Example Ave, New York City">  
    <Rack Name="B07" Location="Aisle B, Rack 07">  
      <Node Name="Server04" Location="Rack Unit 20" />  
      <Node Name="Server05" Location="Rack Unit 22" />  
      <Node Name="Server06" Location="Rack Unit 24" />  
    </Rack>  
  </Site>  
</Topology> 
``` 

#### <a name="example-two-chassis-blade-servers"></a>Beispiel: zwei Gehäuse, Blade Server  
```XML
<Topology>  
  <Rack Name="A01" Location="Contoso HQ, Room 4010, Aisle A, Rack 01">  
    <Chassis Name="Chassis01" Location="Rack Unit 2 (Upper)" >  
      <Node Name="Server01" Location="Left" />  
      <Node Name="Server02" Location="Right" />  
    </Chassis>  
    <Chassis Name="Chassis02" Location="Rack Unit 6 (Lower)" >  
      <Node Name="Server03" Location="Left" />  
      <Node Name="Server04" Location="Right" />  
    </Chassis>  
  </Rack>  
</Topology>  
```

Wenn Sie die neue Fehler Domänen Spezifikation festlegen möchten, speichern Sie Ihre XML-Datei, und führen Sie Folgendes in PowerShell aus.  

```PowerShell
$xml = Get-Content <Path> | Out-String  
Set-ClusterFaultDomainXML -XML $xml
```

Dieses Handbuch enthält nur zwei Beispiele, aber die Tags "`<Site>`", "`<Rack>`", "`<Chassis>`" und "`<Node>`" können gemischt und mit vielen zusätzlichen Möglichkeiten abgeglichen werden, um die physische Topologie Ihrer Bereitstellung widerzuspiegeln. Wir hoffen, dass diese Beispiele die Flexibilität dieser Tags und den Wert der Freiformpositionsdeskriptoren zu ihrer Unterscheidung veranschaulichen.  

### <a name="optional-location-and-description-metadata"></a>Optional: Speicherort und Beschreibungs Metadaten

Sie können optionale **Speicherort** -oder **Beschreibungs** Metadaten für jede Fehler Domäne angeben. Wenn angegeben, werden diese Informationen in Hardwarewarnungen des Integritätsdiensts einbezogen. In diesem kurzen Video wird der Wert für das Hinzufügen solcher Deskriptoren veranschaulicht.

[![Click, um ein kurzes Video zu sehen, das den Wert für das Hinzufügen von Standort Deskriptoren zu Fehler Domänen veranschaulicht](media/Fault-Domains-in-Windows-Server-2016/part-4-location-description.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-4-Location-Description)

## <a name="see-also"></a>Siehe auch  
- [Erste Schritte mit Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/get-started-19)  
- [Beginnen Sie mit Windows Server 2016](https://docs.microsoft.com/windows-server/get-started/server-basics)  
-   [Übersicht über direkte Speicherplätze](../storage/storage-spaces/storage-spaces-direct-overview.md) 
