---
title: Direkte Speicherplätze für die
ms.prod: windows-server
ms.author: jgerend
ms.manager: dansimp
ms.technology: storagespaces
ms.topic: article
author: cosmosdarwin
ms.date: 03/15/2019
ms.openlocfilehash: ea1c4b2c249759634e00f6a1ac2caa34f8085ae1
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402864"
---
# <a name="nested-resiliency-for-storage-spaces-direct"></a>Direkte Speicherplätze für die

> Gilt für: Windows Server 2019

Die geschlagene Resilienz ist eine neue Funktion von [direkte Speicherplätze](storage-spaces-direct-overview.md) in Windows Server 2019, mit der ein Cluster mit zwei Servern gleichzeitig mit mehreren Hardwarefehlern zu tun kann, ohne dass Speicherverfügbarkeit verloren geht, d. h. Benutzer, Apps und virtuelle Computer Führen Sie den Vorgang ohne Unterbrechung fort. In diesem Thema wird erläutert, wie es funktioniert, eine Schritt-für-Schritt-Anleitung für den Einstieg bietet und die am häufigsten gestellten Fragen beantwortet.

## <a name="prerequisites"></a>Erforderliche Komponenten

### <a name="green-checkmark-iconmedianested-resiliencysupportedpng-consider-nested-resiliency-if"></a>![Grünes Häkchen.](media/nested-resiliency/supported.png) Beachten Sie die folgenden Punkte:

- Ihr Cluster führt Windows Server 2019; aus. immer
- Ihr Cluster weist genau 2 Server Knoten auf.

### <a name="red-x-iconmedianested-resiliencyunsupportedpng-you-cant-use-nested-resiliency-if"></a>![Rotes X-Symbol.](media/nested-resiliency/unsupported.png) Es ist nicht möglich, die nicht in der folgenden Einstellung zu verwenden:

- Ihr Cluster führt Windows Server 2016; aus. noch
- Der Cluster verfügt über drei oder mehr Server Knoten.

## <a name="why-nested-resiliency"></a>Gründe für geschlagelte Resilienz

Volumes, die geschlagene Resilienz verwenden, können **online bleiben und zugänglich sein, auch wenn mehrere Hardwarefehler gleichzeitig auftreten**, im Gegensatz zur klassischen bidirektionalen [Spiegelungs](storage-spaces-fault-tolerance.md) Resilienz. Wenn z. b. zwei Laufwerke gleichzeitig ausfallen oder ein Server ausfällt und ein Laufwerk ausfällt, bleiben Volumes, die die geschlagene Resilienz verwenden, Online und zugänglich. Bei einer hyperkonvergierten Infrastruktur erhöht sich dadurch die Betriebszeit für apps und virtuelle Computer. bei Dateiserver-Workloads bedeutet dies, dass Benutzer ununterbrochenen Zugriff auf Ihre Dateien haben.

![Speicherverfügbarkeit](media/nested-resiliency/storage-availability.png)

Der Nachteil besteht darin, dass die **Leistungsfähigkeit der gespiegelten Sicherheit eine geringere Kapazitäts Effizienz aufweist als**bei der klassischen bidirektionalen Spiegelung Weitere Informationen finden Sie unten im Abschnitt [Kapazitäts Effizienz](#capacity-efficiency) .

## <a name="how-it-works"></a>Funktionsweise

### <a name="inspiration-raid-51"></a>Idee RAID 5 + 1

RAID 5 + 1 ist eine bewährte Form der Resilienz verteilter Speicher, die hilfreiche Hintergrundinformationen zur besseren besseren Sicherheit bietet. In RAID 5 + 1 wird die lokale Resilienz innerhalb der einzelnen Server durch RAID-5 oder eine *einzelne Parität*bereitgestellt, um vor dem Verlust einzelner Laufwerke zu schützen. Anschließend wird die Resilienz durch RAID-1 oder die bidirektionale *Spiegelung*zwischen den beiden Servern bereitgestellt, die vor dem Verlust der beiden Server geschützt werden sollen.

![RAID 5 + 1](media/nested-resiliency/raid-51.png)

### <a name="two-new-resiliency-options"></a>Zwei neue Optionen für Resilienz

Direkte Speicherplätze in Windows Server 2019 bietet zwei neue resilienzoptionen, die in der Software implementiert sind, ohne dass spezielle RAID-Hardware erforderlich ist:

- **Die zwei-Wege-Spiegelung.** Auf jedem Server wird die lokale Resilienz durch die bidirektionale Spiegelung bereitgestellt, und dann wird durch die bidirektionale Spiegelung zwischen den beiden Servern eine weitere Resilienz bereitgestellt. Es handelt sich im Wesentlichen um einen vier-Wege-Spiegel mit zwei Kopien auf jedem Server. Die schattenbidirektionale Spiegelung bietet eine kompromisslose Leistung: Schreibvorgänge werden auf alle Kopien durchlaufen, und Lesevorgänge stammen aus beliebigen Kopien.

  ![Zwei-Wege-Spiegelung](media/nested-resiliency/nested-two-way-mirror.png)

- **Gespiegelte gespiegelte Spiegelung.** Kombinieren Sie die geduckte bidirektionale Spiegelung von oben mit der gespiegelten Parität. Innerhalb jedes Servers wird die lokale Resilienz für die meisten Daten durch eine einzelne [bitweise Paritäts Arithmetik](storage-spaces-fault-tolerance.md#parity)bereitgestellt, mit Ausnahme neuer neuer Schreibvorgänge, die die bidirektionale Spiegelung verwenden. Anschließend wird die bidirektionale Spiegelung zwischen den Servern durch die bidirektionale Spiegelung gewährleistet. Weitere Informationen zur Funktionsweise der Spiegel beschleunigten Parität finden Sie unter [Spiegel beschleunigter Parität](https://docs.microsoft.com/windows-server/storage/refs/mirror-accelerated-parity).

  ![Gespiegelte gespiegelte Spiegelung](media/nested-resiliency/nested-mirror-accelerated-parity.png)

### <a name="capacity-efficiency"></a>Kapazitäts Effizienz

Kapazitäts Effizienz ist das Verhältnis zwischen nutzbarem Speicherplatz und [volumenbedarf](plan-volumes.md#choosing-the-size-of-volumes). Es beschreibt den Kapazitäts Aufwand, der auf Resilienz zurückzuführen ist, und hängt von der gewählten resilienzoption ab. Ein einfaches Beispiel: das Speichern von Daten ohne Resilienz beträgt eine Kapazitäts Effizienz von 100% (1 TB an Daten belegt 1 TB physischer Speicherkapazität), während die bidirektionale Spiegelung 50% effizient ist (1 TB an Daten nimmt 2 TB an physischer Speicherkapazität).

- Bei einer schattenten bidirektionalen **Spiegelung** werden vier Kopien von allem geschrieben, was bedeutet, dass Sie eine physische Speicherkapazität von 4 TB benötigen, um 1 TB Daten zu speichern. Obwohl ihre Einfachheit ansprechend ist, ist die Leistungseffizienz der in der bidirektionalen Spiegelung 25% enthaltenen Kapazitäts Effizienz in direkte Speicherplätze der niedrigste Wert für Resilienz.

- Bei einer **gespiegelten, beschleunigten Spiegelung** wird eine höhere Kapazitäts Effizienz erzielt, etwa 35%-40%. Diese hängt von zwei Faktoren ab: der Anzahl der Kapazitäts Laufwerke auf den einzelnen Servern und der Kombination aus Spiegelung und Parität, die Sie für das Volume angeben. Diese Tabelle bietet eine Suche nach allgemeinen Konfigurationen:

  | Kapazitäts Laufwerke pro Server | 10% Spiegelung | 20% Spiegelung | Spiegelung von 30% |
  |----------------------------|------------|------------|------------|
  | 4                          | 35,7%      | 34,1%      | 32,6%      |
  | 5                          | 37,7%      | 35,7%      | 33,9%      |
  | 6                          | 39,1%      | 36,8%      | 34,7%      |
  | 7 +                         | 40,0%      | 37,5%      | 35,3%      |

  > [!NOTE]
  > **Wenn Sie neugierig sind, finden Sie hier ein Beispiel für die vollständige mathematische Version.** Angenommen, wir verfügen über sechs Kapazitäts Laufwerke auf jedem der beiden Server, und wir möchten 1 100 GB-Volumen erstellen, bestehend aus 10 GB Spiegel und 90 GB Parität. Die Server-lokale bidirektionale Spiegelung ist 50,0% effizient, d. h., die 10 GB an Spiegel Daten Verb müssen 20 GB für die Speicherung auf den einzelnen Servern. Der gesamte Speicherbedarf beträgt 40 GB. Server-Local Single Parität, in diesem Fall, ist 5/6 = 83,3% effizient, was bedeutet, dass die 90 GB der Paritäts Daten auf jedem Server 108 GB speichern. Der gesamte Speicherbedarf beträgt 216 GB. Der Gesamt Speicherbedarf beträgt daher [(10 GB/50,0%) + (90 GB/83,3%)] × 2 = 256 GB, für die Gesamt Kapazitäts Effizienz von 39,1%.

Beachten Sie, dass die Kapazitäts Effizienz der klassischen bidirektionalen Spiegelung (ca. 50%) liegt. und der gespiegelten, gespiegelten Spiegelung (bis zu 40%) sind nicht sehr unterschiedlich. Abhängig von Ihren Anforderungen kann die Effizienz der Speicherverfügbarkeit durch eine etwas geringere Kapazitäts Effizienz erheblich gesteigert werden. Sie wählen Resilienz pro Volume aus, sodass Sie geschachtelte resilienzvolumes und klassische bidirektionale Spiegelungs Volumes innerhalb desselben Clusters kombinieren können.

![Kompromiss](media/nested-resiliency/tradeoff.png)

## <a name="usage-in-powershell"></a>Verwendung in PowerShell

Sie können bekannte Storage-Cmdlets in PowerShell verwenden, um Volumes mit der Schattens-Resilienz zu erstellen.

### <a name="step-1-create-storage-tier-templates"></a>Schritt 1: Erstellen von Speicherebenen-Vorlagen

Erstellen Sie zunächst mithilfe des Cmdlets "`New-StorageTier`" neue speicherebenenvorlagen. Sie müssen dies nur einmal durchführen, und dann kann jedes neu erstellte Volume auf diese Vorlage verweisen. Geben Sie den `-MediaType` Ihres Kapazitäts Laufwerks und optional den `-FriendlyName` Ihrer Wahl an. Ändern Sie die anderen Parameter nicht.

Wenn Ihre Kapazitäts Laufwerke Festplattenlaufwerke (HDD) sind, starten Sie PowerShell als Administrator, und führen Sie Folgendes aus:

```PowerShell 
# For mirror
New-StorageTier -StoragePoolFriendlyName S2D* -FriendlyName NestedMirror -ResiliencySettingName Mirror -MediaType HDD -NumberOfDataCopies 4

# For parity
New-StorageTier -StoragePoolFriendlyName S2D* -FriendlyName NestedParity -ResiliencySettingName Parity -MediaType HDD -NumberOfDataCopies 2 -PhysicalDiskRedundancy 1 -NumberOfGroups 1 -FaultDomainAwareness StorageScaleUnit -ColumnIsolation PhysicalDisk 
``` 

Wenn es sich bei den Kapazitäts Laufwerken um SSD (Solid-State Drives) handelt, legen Sie den `-MediaType` stattdessen auf `SSD` fest. Ändern Sie die anderen Parameter nicht.

> [!TIP]
> Überprüfen Sie, ob die Tarife mit `Get-StorageTier` erfolgreich erstellt wurden.

### <a name="step-2-create-volumes"></a>Schritt 2: Erstellen von Volumes

Erstellen Sie dann mit dem Cmdlet "`New-Volume`" neue Volumes.

#### <a name="nested-two-way-mirror"></a>Zwei-Wege-Spiegelung

Wenn Sie eine zwei-Wege-Spiegelung verwenden möchten, verweisen Sie auf die Vorlage "`NestedMirror`" und geben die Größe an. Zum Beispiel:

```PowerShell
New-Volume -StoragePoolFriendlyName S2D* -FriendlyName Volume01 -StorageTierFriendlyNames NestedMirror -StorageTierSizes 500GB
```

#### <a name="nested-mirror-accelerated-parity"></a>Gespiegelte gespiegelte Spiegelung

Verweisen Sie auf die ebenenvorlagen "`NestedMirror`" und "`NestedParity`", und legen Sie zwei Größen fest, eine für jeden Teil des Volumes (Spiegelung zuerst, Parität Sekunde). Führen Sie beispielsweise Folgendes aus, um ein Volume mit einer Größe von 20% mit einer zwei-Wege-Spiegelung und einer 80%-Parität zu 1 500 erstellen:

```PowerShell
New-Volume -StoragePoolFriendlyName S2D* -FriendlyName Volume02 -StorageTierFriendlyNames NestedMirror, NestedParity -StorageTierSizes 100GB, 400GB
```

### <a name="step-3-continue-in-windows-admin-center"></a>Schritt 3: Im Windows Admin Center fortfahren

Volumes, die die Schattens-Resilienz verwenden, werden im [Windows Admin Center](https://docs.microsoft.com/windows-server/manage/windows-admin-center/understand/windows-admin-center) mit eindeutiger Bezeichnung angezeigt, wie im folgenden Screenshot dargestellt. Nachdem Sie erstellt wurden, können Sie Sie mithilfe des Windows Admin Centers wie jedes andere Volume in direkte Speicherplätze verwalten und überwachen.

![](media/nested-resiliency/windows-admin-center.png)

### <a name="optional-extend-to-cache-drives"></a>Optional: Auf Cache Laufwerke erweitern

Mit den Standardeinstellungen schützt die Unterbrechung der Sicherheit vor dem Verlust von mehreren Kapazitäts Laufwerken zur gleichen Zeit oder einem Server und einem Kapazitäts Laufwerk zur gleichen Zeit. Zur Erweiterung dieses Schutzes auf das Zwischenspeichern von [Laufwerken](understand-the-cache.md) ist ein zusätzlicher Aspekt zu beachten: da Cache Laufwerke häufig Lese *-und Schreib* Vorgänge für *mehrere* Kapazitäts Laufwerke bereitstellen, ist die einzige Möglichkeit sicherzustellen, dass Sie den Verlust eines Cache Laufwerks tolerieren können, wenn die der andere Server ist nicht in der Zwischenspeicherung von Schreibvorgängen, sondern wirkt sich auf die Leistung aus.

Um dieses Szenario zu beheben, bietet direkte Speicherplätze die Option zum automatischen Deaktivieren des Schreib Caches, wenn ein Server in einem Cluster mit zwei Servern nicht aktiv ist, und aktiviert dann das Schreiben Zwischenspeichern, sobald der Server wieder aktiv ist. Um routinemäßige Neustarts ohne Leistungseinbußen zuzulassen, wird der Schreib Cache nicht deaktiviert, bis der Server 30 Minuten lang herunter gesetzt wurde. Wenn der Schreib Cache deaktiviert ist, wird der Inhalt des Schreib Caches auf Kapazitäts Geräte geschrieben. Danach kann der Server ein fehlerhafter Cache Gerät auf dem Online Server tolerieren, obwohl Lesevorgänge aus dem Cache verzögert werden oder fehlschlagen, wenn ein Cache Gerät ausfällt.

Um dieses Verhalten (optional) festzulegen, starten Sie PowerShell als Administrator, und führen Sie Folgendes aus:

```PowerShell
Get-StorageSubSystem Cluster* | Set-StorageHealthSetting -Name "System.Storage.NestedResiliency.DisableWriteCacheOnNodeDown.Enabled" -Value "True"
```

Nach der Festlegung auf " **true**" lautet das Cache Verhalten wie folgt:

| Situation                       | Cache Verhalten                           | Kann der Verlust von Cache Laufwerken toleriert werden? |
|---------------------------------|------------------------------------------|--------------------------------|
| Beide Server hoch                 | Cache Lese-und Schreibvorgänge, vollständige Leistung | Ja                            |
| Server nach unten, erste 30 Minuten   | Cache Lese-und Schreibvorgänge, vollständige Leistung | Nein (vorübergehend)               |
| Nach den ersten 30 Minuten          | Nur Cache Lesevorgänge, betroffene Leistung   | Ja (nachdem der Cache auf Kapazitäts Laufwerke geschrieben wurde)                           |

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

### <a name="can-i-convert-an-existing-volume-between-two-way-mirror-and-nested-resiliency"></a>Kann ich ein vorhandenes Volume zwischen der bidirektionalen Spiegelung und der gespiegelten Resilienz konvertieren?

Nein, Volumes können nicht zwischen resilienztypen konvertiert werden. Bei neuen bereit Stellungen auf Windows Server 2019 sollten Sie voraus entscheiden, welcher resilienztyp Ihren Anforderungen am besten entspricht. Wenn Sie ein Upgrade von Windows Server 2016 ausführen, können Sie neue Volumes mit der geclusterte Resilienz erstellen, Ihre Daten migrieren und dann die älteren Volumes löschen.

### <a name="can-i-use-nested-resiliency-with-multiple-types-of-capacity-drives"></a>Kann ich die Sicherheit von Netzwerken mit mehreren Typen von Kapazitäts Laufwerken verwenden?

Ja, geben Sie einfach die `-MediaType` der einzelnen Ebenen in [Schritt 1](#step-1-create-storage-tier-templates) an. Bei nvme, SSD und HDD im gleichen Cluster stellt der nvme z. b. einen Cache bereit, während die beiden beiden Kapazitäten Kapazität bereitstellen: Legen Sie die `NestedMirror`-Ebene auf `-MediaType SSD` und die `NestedParity`-Ebene auf `-MediaType HDD` fest. Beachten Sie in diesem Fall, dass die Kapazitäts Effizienz der Parität nur von der Anzahl von HDD-Laufwerken abhängt, und Sie benötigen mindestens 4 von Ihnen pro Server.

### <a name="can-i-use-nested-resiliency-with-3-or-more-servers"></a>Kann ich die Ausfallsicherheit mit drei oder mehr Servern verwenden?

Nein, nur die geclusterte Resilienz verwenden, wenn Ihr Cluster über genau 2 Server verfügt.

### <a name="how-many-drives-do-i-need-to-use-nested-resiliency"></a>Wie viele Laufwerke benötige ich, um die Sicherheit zu verbrauchen?

Die Mindestanzahl der für direkte Speicherplätze erforderlichen Laufwerke beträgt 4 Kapazitäts Laufwerke pro Server Knoten und 2 Cache Laufwerke pro Server Knoten (sofern vorhanden). Dies ist bei Windows Server 2016 unverändert. Es gibt keine zusätzlichen Anforderungen an die Ausfallsicherheit, und die Empfehlung für die Reservekapazität ist ebenfalls unverändert.

### <a name="does-nested-resiliency-change-how-drive-replacement-works"></a>Ändert sich die durch die Änderung von Netzwerken ersetzende Stabilität?

Nein.

### <a name="does-nested-resiliency-change-how-server-node-replacement-works"></a>Ändert sich die geänderte Resilienz, wie die Server Knoten Ersetzung funktioniert?

Nein. Um einen Server Knoten und seine Laufwerke zu ersetzen, befolgen Sie die folgende Reihenfolge:

1. Außerbetriebnahme der Laufwerke auf dem ausgehenden Server
2. Fügen Sie den neuen Server mit seinen Laufwerken dem Cluster hinzu.
3. Der Speicherpool wird neu ausgeglichen.
4. Entfernen des ausgehenden Servers und seiner Laufwerke

Weitere Informationen finden Sie im Thema [Entfernen von Servern](remove-servers.md) .

## <a name="see-also"></a>Siehe auch

- [Übersicht über direkte Speicherplätze](storage-spaces-direct-overview.md)
- [Grundlegendes zur Fehlertoleranz in direkte Speicherplätze](storage-spaces-fault-tolerance.md)
- [Planen von Volumes in direkte Speicherplätze](plan-volumes.md)
- [Erstellen von Volumes in direkte Speicherplätze](create-volumes.md)
