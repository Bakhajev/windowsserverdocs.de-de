---
ms.assetid: 0f2a7f7b-aca8-4e5d-ad67-4258e88bc52f
title: Neuerungen beim Speicher in Windows Server
ms.prod: windows-server
ms.author: jgerend
ms.manager: dongill
ms.technology: storage
ms.topic: article
author: jasongerend
ms.date: 05/29/2019
ms.openlocfilehash: ffcff036a7e30018e523def055ce3aeb8d30c225
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71365838"
---
# <a name="whats-new-in-storage-in-windows-server"></a>Neuerungen beim Speicher in Windows Server

>Gilt für: Windows Server 2019, Windows Server 2016, Windows Server (halbjährlicher Kanal)

In diesem Thema werden die neuen und geänderten Funktionen im Speicher in den halbjährlichen Kanal Releases von Windows Server 2019, Windows Server 2016 und Windows Server erläutert.

## <a name="whats-new-in-storage-in-windows-server-version-1903"></a>Neuerungen beim Speicher in Windows Server, Version 1903

In dieser Version von Windows Server werden die folgenden Änderungen und Technologien hinzugefügt.

### <a name="storage-migration-service-now-migrates-local-accounts-clusters-and-linux-servers"></a>Der Speichermigrationsdienst kann jetzt lokale Konten, Cluster und Linux-Server migrieren

Mit dem Speichermigrationsdienst können Server einfacher zu einer neueren Version von Windows Server migriert werden. Er bietet ein grafisches Tool, das Daten auf Servern inventarisiert und anschließend die Daten und die Konfiguration auf neuere Server überträgt – ganz ohne Apps oder die Notwendigkeit für Benutzer, irgendetwas zu ändern.

Wenn Sie diese Version von Windows Server zum Orchestrieren von Migrationen verwenden möchten, haben wir für Sie die folgenden Funktionen hinzugefügt:

- Migrieren lokaler Benutzer und Gruppen zum neuen Server
- Migrieren von Speicher von Failoverclustern
- Migrieren von Speicher von einem Linux-Server, der Samba verwendet
- Vereinfachte Synchronisierung von migrierten Freigaben zu Azure mithilfe von Azure-Dateisynchronisierung
- Migrieren zu neuen Netzwerken wie etwa Azure

Weitere Informationen über den Speichermigrationsdienst finden Sie unter [Speichermigrationsdienst – Übersicht](storage-migration-service/overview.md).

### <a name="system-insights-disk-anomaly-detection"></a>System Insights-Datenträger-Anomalieerkennung

[System Insights](../manage/system-insights/overview.md) ist ein Feature zur vorausschauenden Analyse, das lokal Systemdaten von Windows Server analysiert und Einsichten in die Funktionsweise des Servers bietet. Es bietet standardmäßig eine Reihe integrierter Funktionen, wir haben aber die Möglichkeit zum Installieren weiterer Funktionen im Windows Admin Center hinzugefügt, und den Anfang macht die Erkennung von Datenträgeranomalien.

Die Erkennung von Datenträgeranomalien ist eine neue Funktion, die den Fall hervorhebt, dass Datenträger sich *anders* als gewöhnlich verhalten. Zwar ist anders nicht zwangsläufig schlecht, aber die Darstellung der anomalen Momente kann bei der Behandlung von Problemen auf Ihren Systemen eine große Hilfe sein.

Diese Funktion ist auch für Server verfügbar, die Windows Server 2019 ausführen.

### <a name="windows-admin-center-enhancements"></a>Verbesserungen am Windows Admin Center

Eine neue Version von Windows Admin Center wurde veröffentlicht, die Windows Server um neue Funktionen bereichert. Informationen zu den neuesten Features finden Sie unter [Windows Admin Center](../manage/windows-admin-center/understand/windows-admin-center.md).

## <a name="whats-new-in-storage-in-windows-server-2019-and-windows-server-version-1809"></a>Neuerungen beim Speicher in Windows Server 2019 und Windows Server, Version 1809

In dieser Version von Windows Server werden die folgenden Änderungen und Technologien hinzugefügt.

### <a name="manage-storage-with-windows-admin-center"></a>Verwalten von Speicher mit dem Windows Admin Center

[Windows Admin Center](../manage/windows-admin-center/overview.md) ist eine neue lokal bereitgestellte, browserbasierte App zum Verwalten von Servern, Clustern, hyperkonvergierten Infrastrukturen mit direkte Speicherplätze und Windows 10-PCs. Es fallen keine zusätzlichen Kosten über Windows an und ist für die Verwendung in der Produktion bereit.

Um fair zu sein, ist Windows Admin Center ein separater Download, der unter Windows Server 2019 und anderen Versionen von Windows ausgeführt wird. es handelt sich jedoch um einen neuen Download, den wir nicht übersehen möchten...

### <a name="storage-migration-service"></a>Speichermigrationsdienst

Der Speichermigrationsdienst ist eine neue Technologie, mit der Server einfacher auf eine neuere Version von Windows Server migriert werden können. Er bietet ein grafisches Tool, das Daten auf Servern inventarisiert, Daten und Konfiguration auf neuere Server überträgt und dann optional die Identitäten der alten Server auf die neuen Server überträgt, sodass Apps und Benutzer nichts ändern müssen. Weitere Informationen finden Sie unter [Speichermigrationsdienst)](storage-migration-service/overview.md).

### <a id="storage-spaces-direct"></a>Direkte Speicherplätze (nur Windows Server 2019)

Es gibt eine Reihe von Verbesserungen bei der direkte Speicherplätze in Windows Server 2019 (direkte Speicherplätze ist nicht in Windows Server enthalten, halbjährlicher Kanal):

- **Datendeduplizierung und -komprimierung für ReFS-Volumes**

    Speichern Sie bis zu zehnmal mehr Daten auf demselben Volume mit Deduplizierung und Komprimierung für das Refs-Dateisystem. (Es ist [nur ein Mausklick](https://www.youtube.com/watch?v=PRibTacyKko&feature=youtu.be) , um mit dem Windows Admin Center zu aktivieren.) Der Blockspeicher variabler Größe mit optionaler Komprimierung maximiert die Einsparungs Raten, während sich die nach Verarbeitungs Architektur mit mehreren Threads nur minimal auf die Leistung auswirkt. Von werden Volumes mit bis zu 64 TB unterstützt, und die ersten 4 TB der einzelnen Dateien werden dedupliziert.

- **Systemeigene Unterstützung für den dauerhaften Speicher**

    Erhalten Sie beispiellose Leistung mit der systemeigenen Storage Spaces Direct-Unterstützung für persistente Speichermodule, einschließlich Intel® Optane™ DC PM und NVDIMM-N. Verwenden Sie den permanenten Speicher als Cache, um den aktiven Arbeitssatz zu beschleunigen, oder als Kapazität, um eine konsistente niedrige Latenz in der Größenordnung von Mikrosekunden zu gewährleisten. Verwalten Sie persistenten Speicher wie jedes andere Laufwerk in PowerShell oder Windows Admin Center.

- **Verschachtelte Ausfallsicherheit für hyperkonvergente Infrastruktur mit zwei Knoten am Rand**

    Bewältigen Sie zwei Hardwarefehler auf einmal mit einer völlig neuen Software-Resilience-Option, die von RAID 5+1 inspiriert wurde. Mit verschachtelter Ausfallsicherheit kann ein Storage Spaces Direct-Cluster mit zwei Knoten kontinuierlich verfügbaren Speicher für Anwendungen und virtuelle Maschinen bereitstellen, selbst wenn ein Serverknoten ausfällt und ein Laufwerk auf dem anderen Serverknoten ausfällt.

- **Zwei-Servercluster mit einem USB-Speicherstick als Zeuge**

    Verwenden Sie ein kostengünstiges USB-Speicherstick, das in Ihren Router eingebunden ist, um als Zeuge in zwei-Server-Clustern zu fungieren. Wenn ein Server ausfällt und anschließend wieder hochgefahren wird, weiß der USB-Laufwerk Cluster, welcher Server über die aktuellsten Daten verfügt. Weitere Informationen finden Sie im [Blog zu Storage bei Microsoft](https://blogs.technet.microsoft.com/filecab/2018/06/27/windows-server-summit-recap/).

- **Windows Admin Center**

    Verwalten und überwachen Sie Storage Spaces Direct mit dem neuen [Dashboard](../manage/windows-admin-center/use/manage-hyper-converged.md), das speziell für Windows entwickelt wurde, und erleben Sie Windows Admin Center. Erstellen, öffnen, erweitern oder löschen Sie Volumes mit nur wenigen Klicks. Überwachen Sie die Leistung wie IOPS und IO-Latenz vom gesamten Cluster bis hinunter zur einzelnen SSD oder HDD. Ohne zusätzliche Kosten für Windows Server 2016 und Windows Server 2019 verfügbar.

- **Leistungsverlauf**

    Erhalten Sie einen mühelosen Einblick in die Ressourcennutzung und -leistung mit [integriertem Verlauf](storage-spaces/performance-history.md). Über 50 wichtige Leistungsindikatoren, die Rechen-, Speicher-, Netzwerk- und Speicherfunktionen umfassen, werden automatisch für bis zu einem Jahr im Cluster gesammelt und gespeichert. Am besten ist es, nichts zu installieren, zu konfigurieren oder zu starten – es funktioniert einfach. Visualisieren Sie in Windows Admin Center oder führen Sie Abfragen oder Verarbeitungen in PowerShell durch

- **Skalieren bis zu 4 PB pro Cluster**

    Erzielen Sie eine Multi-Petabyte-Skalierung - ideal für Medien-, Backup- und Archivierungsfälle. In Windows Server 2019 unterstützt Storage Spaces Direct bis zu 4 Petabyte (PB) = 4.000 Terabyte Rohkapazität pro Speicherpool. Die zugehörigen Kapazitätsrichtlinien werden ebenfalls erhöht: Sie können beispielsweise doppelt so viele Volumes (64 statt 32) erstellen, jeweils doppelt so groß wie zuvor (64 TB statt 32 TB). Gruppieren Sie mehrere Cluster in einem [Cluster Satz](storage-spaces/cluster-sets.md) für eine noch größere Skalierung innerhalb eines Speicher Namespace. Weitere Informationen finden Sie im [Blog zu Storage bei Microsoft](https://blogs.technet.microsoft.com/filecab/2018/06/27/windows-server-summit-recap/).

- **Durch Spiegelung beschleunigte Parität mit doppelter Geschwindigkeit**

    Mit einer Spiegel-beschleunigten Parität können Sie Storage Spaces Direct-Volumes erstellen, die teilweise Spiegel- und Teileparität sind, wie das Mischen von RAID-1 und RAID-5/6, um das Beste aus beiden zu erhalten. (Es ist [einfacher, als Sie](https://www.youtube.com/watch?v=R72QHudqWpE) im Windows Admin Center nachzudenken.) In Windows Server 2019 ist die Leistung der Spiegel beschleunigten Parität bei Windows Server 2016 aufgrund von Optimierungen größer als verdoppelt.

- **Erkennung von Laufwerkslatenz-Ausreißern**

    Identifizieren Sie mühelos Laufwerke mit nicht normaler Latenz bei der proaktiven Überwachung und der integrierten Ausreißererkennung, die durch den langfristigen und erfolgreichen Ansatz der Microsoft Azure inspiriert sind. Unabhängig davon, ob es sich um eine durchschnittliche Latenz oder um eine feinere Latenz wie die 99. Perzentil-Wartezeit handelt, werden langsame Laufwerke automatisch in PowerShell und Windows Admin Center mit dem Status "ungewöhnliche Latenz" bezeichnet.

- **Manuelle Begrenzung der Volumenzuweisung zur Erhöhung der Fehlertoleranz**

    Dadurch können Administratoren die Zuordnung von Volumes in direkte Speicherplätze manuell begrenzen. Dadurch kann die Fehlertoleranz unter bestimmten Bedingungen erheblich erhöht werden, es werden jedoch einige zusätzliche Überlegungen zur Verwaltung und Komplexität auferlegt. Weitere Informationen finden Sie unter [begrenzen der Zuordnung von Volumes](storage-spaces/delimit-volume-allocation.md).

### <a name="storage-replica2019"></a>Speicher Replikat

In dieser Version gibt es eine Reihe von Verbesserungen für das [Speicher Replikat](storage-replica/storage-replica-overview.md) :

#### <a name="storage-replica-in-windows-server-standard-edition"></a>Speicher Replikat in Windows Server Standard Edition

Sie können jetzt das Speicher Replikat mit Windows Server Standard Edition zusätzlich zu Datacenter Edition verwenden. Das Speicher Replikat, das unter Windows Server Standard Edition ausgeführt wird, weist die folgenden Einschränkungen auf:

- Das Speicher Replikat repliziert ein einzelnes Volume anstelle einer unbegrenzten Anzahl von Volumes.
- Volumes können eine Größe von bis zu 2 TB anstelle einer unbegrenzten Größe aufweisen.

#### <a name="storage-replica-log-performance-improvements"></a>Verbesserungen der Protokollierungsleistung für Speicherreplikate

Wir haben außerdem Verbesserungen an der Nachverfolgung der Replikation durch das Speicher Replikat Protokoll vorgenommen, um den Replikations Durchsatz und die Latenz zu verbessern. Dies gilt insbesondere für den gesamten Flash Speicher sowie für die direkte Speicherplätze

Um die Leistungssteigerung zu erzielen, müssen alle Mitglieder der Replikations Gruppe Windows Server 2019 ausführen.

#### <a name="test-failover"></a>Testen des Failovers

Sie können jetzt vorübergehend eine Momentaufnahme des replizierten Speichers auf einem Zielserver für Test-oder Sicherungszwecke einbinden. Weitere Informationen finden Sie unter [Häufig gestellte Fragen zu Speicherreplikaten](https://aka.ms/srfaq).

#### <a name="windows-admin-center-support"></a>Support für Windows Admin Center

Die Unterstützung für die grafische Verwaltung der Replikation ist jetzt über das Server-Manager Tool im Windows Admin Center verfügbar. Dies schließt die Server-zu-Server-Replikation, Cluster-zu-Cluster sowie die Stretch-Cluster Replikation ein.

#### <a name="miscellaneous-improvements"></a>Sonstige Verbesserungen

Das Speicher Replikat enthält auch folgende Verbesserungen:

-   Ändert das Verhalten von asynchronen streckungs Clustern, sodass automatische Failover jetzt auftreten
-   Mehrere Fehlerbehebungen

### <a name="smb"></a>SMB

- **SMB1 und das Entfernen der Gastauthentifizierung**: Der Server Message Block-Client und-Server werden von Windows Server nicht mehr standardmäßig installiert. Darüber hinaus ist die Möglichkeit deaktiviert, sich als Gast in SMB2 und höher standardmäßig zu authentifizieren. Weitere Informationen finden Sie unter [SMBv1 wird für Windows 10, Version 1709, und Windows Server, Version 1709, standardmäßig nicht installiert](https://support.microsoft.com/help/4034314/smbv1-is-not-installed-by-default-in-windows-10-rs3-and-windows-server). 

- **SMB2/SMB3-Sicherheit und Kompatibilität**: Es wurden zusätzliche Optionen für die Sicherheits- und Anwendungskompatibilität hinzugefügt, einschließlich der Möglichkeit, Oplocks SMB2+ für Legacy-Anwendungen zu deaktivieren, sowie die Signierung oder Verschlüsselung, die auf Basis jeder einzelnen Verbindung von einem Client erforderlich ist. Weitere Informationen finden Sie in der SMBShare PowerShell-Modul-Hilfe.

### <a name="data-deduplication"></a>Datendeduplizierung

- **Datendeduplizierung unterstützt jetzt ReFS**: Sie müssen nicht mehr zwischen den Vorteilen eines modernen Dateisystems mit ReFS und der Datendeduplizierung wählen: Sie können jetzt die Datendeduplizierung aktivieren, überall wo ReFS aktiviert werden kann. Erhöhen Sie die Speichereffizienz von schätzungsweise mehr als 95 % mit ReFS.
- **DataPort-API für den optimierten Eingang/Ausgang von deduplizierten Volumes**: Entwickler können jetzt die Kenntnisse der Datendeduplizierung zum effizienten Speichern von Daten, zum Verschieben von Daten zwischen Volumes, Servern und Clustern effizient nutzen.

### <a name="file-server-resource-manager"></a>Ressourcen-Manager für Dateiserver

Windows Server 2019 bietet die Möglichkeit, zu verhindern, dass der Datei Server Ressourcen-Manager Dienstanbieter ein Änderungs Journal (auch als USN-Journal bezeichnet) auf allen Volumes erstellt, wenn der Dienst gestartet wird. Dies kann Speicherplatz auf jedem Datenträger sparen, deaktiviert allerdings in Echtzeit die Dateiklassifizierung. Weitere Informationen finden Sie unter [Übersicht über den Ressourcen-Manager für Dateiserver](fsrm/fsrm-overview.md).

## <a name="whats-new-in-storage-in-windows-server-version-1803"></a>Neuerungen beim Speicher in Windows Server, Version 1803

### <a name="file-server-resource-manager"></a>Ressourcen-Manager für Dateiserver

Windows Server, Version 1803, bietet die Möglichkeit, zu verhindern, dass der Datei Server Ressourcen-Manager Dienstanbieter ein Änderungs Journal (auch als USN-Journal bezeichnet) auf allen Volumes erstellt, wenn der Dienst gestartet wird. Dies kann Speicherplatz auf jedem Datenträger sparen, deaktiviert allerdings in Echtzeit die Dateiklassifizierung. Weitere Informationen finden Sie unter [Übersicht über den Ressourcen-Manager für Dateiserver](fsrm/fsrm-overview.md).

## <a name="whats-new-in-storage-in-windows-server-version-1709"></a>Neuerungen beim Speicher in Windows Server, Version 1709

Windows Server, Version 1709, ist die erste Version von Windows Server im halbjährlichen Kanal. Der halbjährliche Kanal ist ein Software Assurance-Vorteil, der in der Produktion 18 Monate lang vollständig unterstützt wird, mit einer neuen Version alle sechs Monate.

Weitere Informationen finden Sie unter [Übersicht: Windows Server, Semi-Annual Channel](../get-started/semi-annual-channel-overview.md).

### <a name="storage-replica"></a>Speicherreplikat

Der durch das Speicher Replikat hinzugefügte Schutz durch die Notfall Wiederherstellung wird nun erweitert

- **Testen des Failovers**: die Option zum Bereitstellen des Ziel-Speichers ist jetzt mit der Funktion zum Testen des Failovers möglich. Sie können eine Momentaufnahme des replizierten Speichers auf Zielknoten vorübergehend zu Test- und Sicherungszwecken bereitstellen. Weitere Informationen finden Sie unter [Häufig gestellte Fragen zu Speicherreplikaten](https://aka.ms/srfaq).
- **Windows Admin Center-Unterstützung**: Die Unterstützung für die grafische Verwaltung der Replikation ist jetzt über das Server-Manager Tool im Windows Admin Center verfügbar. Dies schließt die Server-zu-Server-Replikation, Cluster-zu-Cluster sowie die Stretch-Cluster Replikation ein.

Das Speicher Replikat enthält auch folgende Verbesserungen:

-   Ändert das Verhalten von asynchronen streckungs Clustern, sodass automatische Failover jetzt auftreten
-   Mehrere Fehlerbehebungen

### <a name="smb"></a>SMB

- **SMB1 und das Entfernen der Gastauthentifizierung**: In Windows Server, Version 1709, wird der SMB1-Client und -Server nicht mehr standardmäßig installiert. Darüber hinaus ist die Möglichkeit deaktiviert, sich als Gast in SMB2 und höher standardmäßig zu authentifizieren. Weitere Informationen finden Sie unter [SMBv1 wird für Windows 10, Version 1709, und Windows Server, Version 1709, standardmäßig nicht installiert](https://support.microsoft.com/help/4034314/smbv1-is-not-installed-by-default-in-windows-10-rs3-and-windows-server). 

- **SMB2/SMB3-Sicherheit und Kompatibilität**: Es wurden zusätzliche Optionen für die Sicherheits- und Anwendungskompatibilität hinzugefügt, einschließlich der Möglichkeit, Oplocks SMB2+ für Legacy-Anwendungen zu deaktivieren, sowie die Signierung oder Verschlüsselung, die auf Basis jeder einzelnen Verbindung von einem Client erforderlich ist. Weitere Informationen finden Sie in der SMBShare PowerShell-Modul-Hilfe.

### <a name="data-deduplication"></a>Datendeduplizierung

- **Datendeduplizierung unterstützt jetzt ReFS**: Sie müssen nicht mehr zwischen den Vorteilen eines modernen Dateisystems mit ReFS und der Datendeduplizierung wählen: Sie können jetzt die Datendeduplizierung aktivieren, überall wo ReFS aktiviert werden kann. Erhöhen Sie die Speichereffizienz von schätzungsweise mehr als 95 % mit ReFS.
- **DataPort-API für den optimierten Eingang/Ausgang von deduplizierten Volumes**: Entwickler können jetzt die Kenntnisse der Datendeduplizierung zum effizienten Speichern von Daten, zum Verschieben von Daten zwischen Volumes, Servern und Clustern effizient nutzen.

## <a name="whats-new-in-storage-in-windows-server-2016"></a>Neuerungen beim Speicher in Windows Server 2016

### <a name="s2d"></a>Direkte Speicherplätze  
Mit direkten Speicherplätzen kann hoch verfügbarer und skalierbarer Speicher unter Verwendung von Servern mit lokalem Speicher erstellt werden. Mit diesem Feature wird die Bereitstellung und die Verwaltung von softwaredefinierten Speichersystemen vereinfacht und auch der Weg zur Nutzung neuer Datenträgerklassen wie z. B. SATA-SSD und NVMe geebnet, was vorher bei gruppierten Speicherplätzen mit freigegebenen Datenträgern nicht möglich war.  

**Welchen Nutzen bietet diese Änderung?**  
Mit direkten Speicherplätzen können Dienstanbieter und Unternehmen Server nach Industriestandard mit lokalem Speicher einsetzen, um hoch verfügbare und skalierbare softwaredefinierte Speichersysteme zu erstellen. Die Verwendung von Servern mit lokalem Speicher führt zu weniger Komplexität, höherer Skalierbarkeit und der Möglichkeit, Speichergeräte zu nutzen, die zuvor nicht verwendet werden konnten (z. B. SATA-SSDs zum Senken der Kosten von Flash-Speicher oder NVMe-SSDs für eine höhere Leistung).  

Bei Verwendung von direkten Speicherplätzen wird kein gemeinsames SAS-Fabric benötigt, sodass die Bereitstellung und die Konfiguration vereinfacht werden. Stattdessen wird das Netzwerk als Speicherfabric genutzt. Dabei kommen SMB3 und SMB Direct (RDMA) zum Einsatz, um Speicher mit hoher Geschwindigkeit, geringer Latenz und hoher CPU-Effizienz bereitzustellen. Für eine horizontale Hochskalierung fügen Sie ganz einfach weitere Server hinzu, um die Speicherkapazität und die E/A-Leistung zu steigern.  
Weitere Informationen finden Sie unter [Direkte Speicherplätze in Windows Server 2016](storage-spaces/storage-spaces-direct-overview.md).  

**Worin bestehen die Unterschiede?**  
Dies ist eine neue Funktion in Windows Server 2016.  

### <a name="storage-replica"></a>Speicher Replikat

Speicherreplikat ermöglicht eine speicheragnostische, synchrone Replikation auf Blockebene zwischen Servern oder Clustern für die Notfallwiederherstellung sowie das Strecken eines Failoverclusters zwischen Standorten. Die synchrone Replikation ermöglicht die Spiegelung von Daten an physischen Standorten mit ausfallsicheren Volumes, um auf Dateisystemebene sicherzustellen, dass kein Datenverlust auftritt. Die asynchrone Replikation ermöglicht die Standorterweiterung über regionale Bereiche hinaus mit der Möglichkeit von Datenverlusten.  

**Welchen Nutzen bietet diese Änderung?**  
Mithilfe der Speicherreplikation können Sie folgende Ziele erreichen:  

* Bereitstellen einer Notfallwiederherstellungslösung von einem einzigen Anbieter für geplante und ungeplante Ausfälle unternehmenskritischer Workloads.
* Verwenden des SMB3-Transportprotokolls mit bewährter Zuverlässigkeit, Skalierbarkeit und Leistung.
* Strecken von Windows-Failoverclustern über regionale Bereiche hinweg.
* Einsatz von Microsoft-Software für die gesamte Speicher- und Clusterumgebung. Dazu zählen Hyper-V, Speicherreplikate, Speicherplätze, Cluster, Dateiserver mit horizontaler Skalierung, SMB3, Deduplizierung und ReFS/NTFS.
* Aufgrund der folgenden Merkmale können Sie die Kosten und die Komplexität senken: 
    * Hardwareagnostisches System, das keine spezifische Speicherkonfiguration wie DAS oder SAN benötigt.
    * Möglichkeit, allgemeine Speicher- und Netzwerktechnologien zu nutzen.
    * Problemlose grafische Verwaltung für einzelne Knoten und Cluster über den Failovercluster-Manager.
    * Umfangreiche Skriptoptionen über Windows PowerShell. 
* Weniger Downtime sowie höhere Zuverlässigkeit und Produktivität dank Windows.  
* Unterstützbarkeit, Leistungsmetriken und Diagnosefunktionen.  

Weitere Informationen finden Sie unter [Speicherreplikate in Windows Server 2016](storage-replica/storage-replica-overview.md).  

**Worin bestehen die Unterschiede?**  
Dies ist eine neue Funktion in Windows Server 2016.  

### <a name="storage-qos"></a>Speicher Quality of Service  
Sie können Quality of Service (QoS) für Speicher jetzt nutzen, um die End-to-End-Speicherleistung zu überwachen und Verwaltungsrichtlinien unter Verwendung von Hyper-V- und CSV-Clustern in Windows Server 2016 zu erstellen.  

**Welchen Nutzen bietet diese Änderung?**  
Sie können nun Speicher-QoS-Richtlinien auf einem CSV-Cluster erstellen und diese einem oder mehreren virtuellen Datenträgern auf virtuellen Hyper-V-Computern zuweisen. Bei Änderungen des Workloads und der Speicherlast wird die Speicherleistung automatisch neu angepasst, um die Richtlinien einzuhalten.  

* In jeder Richtlinie kann ein Reservewert (Minimum) und/oder ein Grenzwert (Maximum) festgelegt werden, der auf eine Sammlung von Datenflüssen angewendet wird (z. B. auf eine virtuelle Festplatte, auf einen einzelnen virtuellen Computer oder eine Gruppe virtueller Computer, auf einen Dienst oder auf einen Mandanten).  
* Über Windows PowerShell oder WMI können die folgenden Aufgaben ausgeführt werden:  
    * Erstellen von Richtlinien auf einem CSV-Cluster
    * Auflisten von Richtlinien auf einem CSV-Cluster
    * Zuweisen einer Richtlinie zu einer virtuellen Festplatte eines virtuellen Hyper-V-Computers 
    * Überwachen der Leistung der einzelnen Flüsse und Status innerhalb der Richtlinie  
* Wenn mehrere virtuelle Festplatten dieselbe Richtlinie verwenden, wird die Leistung gleichmäßig verteilt, um die Mindest- und Höchstwerte der Richtlinien einzuhalten. Daher kann eine Richtlinie zum Verwalten einer virtuellen Festplatte, eines virtuellen Computers, mehrerer virtueller Computer, die einen Dienst umfassen, oder aller virtuellen Computer, die zu einem Mandanten gehören, genutzt werden.  

**Worin bestehen die Unterschiede?**  
Dies ist eine neue Funktion in Windows Server 2016. Das Verwalten von Mindestreserven, das Überwachung von Flüssen aller virtuellen Festplatten im Cluster über einen einzigen Befehl und die zentralisierte, richtlinienbasierte Verwaltung waren in früheren Versionen von Windows Server nicht möglich.  

Weitere Informationen finden Sie unter [Storage Quality of Service](storage-qos/storage-qos-overview.md) (Speicher-QoS).

### <a name="dedup"></a>Datendeduplizierung  
| Funktionalität | Neu oder aktualisiert | Beschreibung |
|---------------|----------------|-------------|
| [Unterstützung für große Volumes](data-deduplication/whats-new.md#large-volume-support) | Aktualisiert | Vor Windows Server 2016 musste die Größe der Volumes speziell für die erwartete Änderung konfiguriert werden, wobei Volumes mit über 10 TB keine geeigneten Kandidaten für die Deduplizierung waren. In Windows Server 2016 unterstützt die Datendeduplizierung Volumegrößen von **bis zu 64 TB**. |
| [Unterstützung für große Dateien](data-deduplication/whats-new.md#large-file-support) | Aktualisiert | Vor Windows Server 2016 waren Dateien mit einer Größe von knapp 1 TB keine geeigneten Kandidaten für die Deduplizierung. In Windows Server 2016 werden Dateien mit einer Größe von **bis zu 1 TB** vollständig unterstützt. |
| [Unterstützung für Nano Server](data-deduplication/whats-new.md#nano-server-support) | Neu | Die Datendeduplizierung ist in der neuen Nano Server-Bereitstellungsoption für Windows Server 2016 verfügbar und wird von dieser Option vollständig unterstützt. |
| [Vereinfachte Unterstützung von Sicherungen](data-deduplication/whats-new.md#simple-backup-support) | Neu | In Windows Server 2012 R2 mussten eine Reihe manueller Konfigurationsschritte ausgeführt werden, um virtualisierte Sicherungsanwendungen wie Microsoft [Data Protection Manager](https://technet.microsoft.com/library/hh758173.aspx) zu unterstützten. In Windows Server 2016 wurde ein neuer Standardverwendungstyp „Sicherung“ hinzugefügt, um eine nahtlose Bereitstellung der Datendeduplizierung für virtualisierte Sicherungsanwendungen zu ermöglichen. |
| [Unterstützung für parallele Upgrades des Cluster Betriebssystems](data-deduplication/whats-new.md#cluster-upgrade-support) | Neu | Die Datendeduplizierung bietet vollständige Unterstützung für das neue Feature für [parallele Upgrades des Clusterbetriebssystems](..//failover-clustering/cluster-operating-system-rolling-upgrade.md) von Windows Server 2016. |

### <a name="smb-hardening-improvements"></a>SMB-Härtungs Verbesserungen für SYSVOL-und Netlogon-Verbindungen  
In Windows 10 und Windows Server 2016 ist für Clientverbindungen mit den SYSVOL- und NETLOGON-Standardfreigaben von Active Directory Domain Services jetzt die SMB-Signierung und gegenseitige Authentifizierung (z. B. Kerberos) erforderlich.   

**Welchen Nutzen bietet diese Änderung?**  
Durch diese Änderung wird die Wahrscheinlichkeit von Man-in-the-Middle-Angriffen verringert.   

**Worin bestehen die Unterschiede?**  
Wenn die SMB-Signierung und die gegenseitige Authentifizierung nicht verfügbar sind, kann ein Computer mit Windows 10 oder Windows Server 2016 keine domänenbasierten Gruppenrichtlinien und Skripts verarbeiten.  

> [!NOTE]  
> Die Registrierungswerte für diese Einstellungen sind standardmäßig nicht verfügbar, die Härtungsregeln gelten jedoch trotzdem, bis sie von Gruppenrichtlinien oder anderen Registrierungswerten außer Kraft gesetzt werden.  

Weitere Informationen zu diesen Sicherheitsverbesserungen (auch als UNC-Härtung bezeichnet) finden Sie im Microsoft Knowledge Base-Artikel [3000483](https://support.microsoft.com/kb/3000483) und [MS15-011 & MS15-014: Gruppenrichtlinie für Härtung](https://blogs.technet.microsoft.com/srd/2015/02/10/ms15-011-ms15-014-hardening-group-policy).  

### <a name="work-folders"></a>Arbeitsordner
Verbesserte Änderungs Benachrichtigung, wenn auf dem Arbeitsordner Server Windows Server 2016 und der Arbeitsordner Client Windows 10 ausgeführt wird.

**Welchen Nutzen bietet diese Änderung?**<br>
Werden unter Windows Server 2012 R2 Dateiänderungen auf die Arbeitsordner-Server synchronisiert, werden die Clients nicht über die Änderung benachrichtigt, und es dauert bis zu 10 Minuten, bis die Aktualisierungen verfügbar sind.  Bei Verwendung von Windows Server 2016 benachrichtigt der Arbeitsordner Server sofort Windows 10-Clients, und die Dateiänderungen werden sofort synchronisiert.

**Worin bestehen die Unterschiede?**<br>
Dies ist eine neue Funktion in Windows Server 2016. Dies erfordert einen Arbeitsordner-Server mit Windows Server 2016 und einen Client mit Windows 10.

Wenn Sie einen älteren Client verwenden oder wenn auf dem Arbeitsordnerserver Windows Server 2012 R2 ausgeführt wird, sucht der Client weiterhin alle zehn Minuten nach Änderungen.

### <a name="refs"></a>ReFS 
Die nächste Iteration von ReFS unterstützt umfangreiche Speicherbereitstellungen mit unterschiedlichen Workloads und bietet Zuverlässigkeit, Resilienz und Skalierbarkeit für Ihre Daten.     

**Welchen Nutzen bietet diese Änderung?**<br>
ReFS sorgt für folgende Verbesserungen:

* ReFS implementiert neue Funktionen für Speicherebenen, die eine höhere Leistung und Speicherkapazität ermöglichen. Diese neuen Funktionen ermöglichen Folgendes:
    * Mehrere Resilienztypen für den gleichen virtuellen Datenträger (beispielsweise mit Spiegelung auf der Leistungsebene und Parität auf der Kapazitätsebene).
    * Schnellere Reaktion auf driftende Workingsets.  
* Die Einführung von Block Cloning hat eine erhebliche Verbesserung der Leistung von VM-Vorgängen zur Folge, was sich beispielsweise bei der Zusammenführung von VHDX-Prüfpunkten bemerkbar macht.
* Das neue ReFS-Überprüfungsprogramm ermöglicht die Behandlung von Speicherverlusten und schützt Daten vor kritischen Beschädigungen. 

**Worin bestehen die Unterschiede?**<br>
Diese Funktionen sind neu in Windows Server 2016. 

## <a name="see-also"></a>Siehe auch  
* [Neuerungen in Windows Server 2016](../get-started/what-s-new-in-windows-server-2016.md)  
