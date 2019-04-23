---
title: Remote Desktop-Gateways die Optimierung der Leistung
description: Empfehlungen für Remote Desktop-Gateways zur leistungsoptimierung
ms.prod: windows-server-threshold
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: HammadBu; VladmiS
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 7619d2e2ce394c7f06826d6ebe36bccfa43344ad
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59842571"
---
# <a name="performance-tuning-remote-desktop-gateways"></a>Remote Desktop-Gateways die Optimierung der Leistung

**Beachten Sie**    Remotedesktopgateway (RD-Gateway) In Windows 8 und höher und Windows Server 2012 R2 oder höher wird unterstützt, TCP, UDP und dem älteren RPC-Transport. Die meisten der folgenden Daten bezieht sich auf den alten RPC-Transport. Wenn Sie nicht der alte RPC-Transport verwendet wird, ist in diesem Abschnitt nicht anwendbar.

Dieses Thema beschreibt die Parameter, mit denen die Leistung einer Bereitstellung für Kunden zu verbessern und die Feinabstimmungen, die auf des Kunden Netzwerk von Verwendungsmustern basieren.

Im Grunde führt RD-Gateway viele Pakete, die Weiterleitung zwischen Instanzen von Remotedesktopverbindung und der RD-Sitzungshost-Server-Instanzen im Netzwerk des Kunden.

**Beachten Sie**    die folgenden Parameter gelten für nur RPC-Transport.

Exportieren die folgenden Registrierungsparameter zur Verbesserung der Systemleistung in das RD-Gateway, Internet Information Services (IIS) und RD-Gateway.

**Thread Feinabstimmungen**

-   **MaxIoThreads**

    ``` syntax
    HKLM\Software\Microsoft\Terminal Server Gateway\Maxiothreads (REG_DWORD)
    ```

    Dieser app-spezifische-Threadpool gibt die Anzahl der Threads, die RD-Gateway erstellt werden, um eingehende Anforderungen zu verarbeiten. Wenn diese Einstellung in der Registrierung vorhanden ist, wird es wirksam. Die Anzahl von Threads entspricht die Anzahl der logischen Prozesse. Wenn die Anzahl der logischen Prozessoren auf weniger als 5 ist, ist die Standardeinstellung 5 Threads.

-   **MaxPoolThreads**

    ``` syntax
    HKLM\System\CurrentControlSet\Services\InetInfo\Parameters\MaxPoolThreads (REG_DWORD)
    ```

    Dieser Parameter gibt die Anzahl der IIS-Pool-Threads pro logischem Prozessor zu erstellen. Die IIS-Pool-Threads sehen Sie sich das Netzwerk für Anforderungen und alle eingehende Anforderungen zu verarbeiten. Die **MaxPoolThreads** Anzahl beinhaltet nicht die Threads, der RD-Gateway verwendet. Der Standardwert lautet %%amp;quot;4%%amp;quot;.

**Remoteprozeduraufruf Aufruf Feinabstimmungen für RD-Gateway**

Die folgenden Parameter können die Remoteprozeduraufrufe (RPC) zu optimieren, die von der Remotedesktopverbindung und RD-Gateway-Computern empfangen werden. Ändern den Windows können einschränken, wie viele Daten fließen über jede Verbindung, und können die Leistung für RPC über HTTP-v2-Szenarien verbessern.

-   **ServerReceiveWindow**

    ``` syntax
    HKLM\Software\Microsoft\Rpc\ServerReceiveWindow (REG_DWORD)
    ```

    Der Standardwert ist 64 KB. Dieser Wert gibt an, das Fenster, das der Server für die Daten verwendet, die von der RPC-Proxy empfangen wird. Der minimale Wert auf 8 KB festgelegt ist, und der maximale Wert auf 1 GB festgelegt ist. Wenn ein Wert nicht vorhanden ist, wird der Standardwert verwendet. Wenn dieser Wert geändert wird, muss IIS neu gestartet werden, für die Änderung wirksam wird.

-   **ServerReceiveWindow**

    ``` syntax
    HKLM\Software\Microsoft\Rpc\ServerReceiveWindow (REG_DWORD)
    ```

    Der Standardwert ist 64 KB. Dieser Wert gibt an, das Fenster, das der Client für die Daten verwendet, die von der RPC-Proxy empfangen wird. Der minimale Wert beträgt 8 KB, und der maximale Wert beträgt 1 GB. Wenn ein Wert nicht vorhanden ist, wird der Standardwert verwendet.

## <a name="monitoring-and-data-collection"></a>Überwachung und Datensammlung


Die folgende Liste von Leistungsindikatoren gilt einen Basissatz von Leistungsindikatoren, wenn Sie die Ressourcenverwendung auf dem RD-Gateway überwachen:

-   \\Terminal Service Gateway\\\*

-   \\RPC/HTTP-Proxy\\\*

-   \\RPC/HTTP-Proxys pro Server\\\*

-   \\Webdienst\\\*

-   \\W3SVC\_W3WP\\\*

-   \\IPv4\\\*

-   \\Arbeitsspeicher\\\*

-   \\Netzwerkschnittstelle (\*)\\\*

-   \\Prozess (\*)\\\*

-   \\Prozessorinformationen (\*)\\\*

-   \\Synchronisierung (\*)\\\*

-   \\System\\\*

-   \\TCPv4\\\*

Die folgenden Leistungsindikatoren gelten nur für ältere RPC-Transport:

-   \\RPC/HTTP-Proxy\\ \* RPC

-   \\RPC/HTTP-Proxys pro Server\\ \* RPC

-   \\Webdienst-\\ \* RPC

-   \\W3SVC\_W3WP\\\* RPC

**Beachten Sie**    fügen Sie ggf. die \\IPv6\\ \* und \\TCPv6\\ \* Objekte. ### ReplaceThisText

 