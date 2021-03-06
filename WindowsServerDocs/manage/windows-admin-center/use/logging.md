---
title: Protokollierung
description: Ereignisprotokollierung vom Windows Admin Center (Project Honolulu)
ms.technology: manage
ms.topic: article
author: haley-rowland
ms.author: harowl
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 012c2229fb29aa711d9887f28859e09bcf71c14a
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71356869"
---
# <a name="use-event-logging-in-windows-admin-center-to-gain-insight-into-management-activities-and-track-gateway-usage"></a>Verwenden Sie die Ereignisprotokollierung im Windows Admin Center, um Einblicke in Verwaltungsaktivitäten zu erhalten und die gatewayverwendung

>Gilt für: Windows Admin Center, Windows Admin Center-Vorschau

Windows Admin Center schreibt Ereignisprotokolle, damit Sie die Verwaltungsaktivitäten anzeigen können, die auf den Servern in Ihrer Umgebung ausgeführt werden, und um Ihnen bei der Behebung von Problemen mit dem Windows Admin Center zu helfen.

## <a name="gain-insight-into-management-activities-in-your-environment-through-user-action-logging"></a>Gewinnen Sie mithilfe der Protokollierung von Benutzeraktionen Einblicke in die Verwaltungsaktivitäten in Ihrer Umgebung.

Das Windows Admin Center bietet Einblick in die Verwaltungsaktivitäten, die auf den Servern in Ihrer Umgebung ausgeführt werden, indem Aktionen im Ereignisprotokoll des verwalteten Servers im Ereignisprotokoll des verwalteten Servers auf dem **Microsoft-servermanagementexperience** -Ereignis Kanal protokolliert werden, mit EventID 4000 und das Quell-smegateway. Das Windows Admin Center protokolliert nur Aktionen auf dem verwalteten Server, sodass keine Ereignisse protokolliert werden, wenn ein Benutzer für schreibgeschützte Zwecke auf einen Server zugreift.

Zu den protokollierten Ereignissen gehören die folgenden Informationen:

| Key           | Wert                                                                                              |
|---------------|----------------------------------------------------------------------------------------------------|
| PowerShell    | Der Name des PowerShell-Skripts, der auf dem Server ausgeführt wurde, wenn die Aktion ein PowerShell-Skript ausgeführt hat. |
| GERUFEN           | CIM-Befehl, der auf dem Server ausgeführt wurde, wenn die Aktion einen CIM-Befehl ausgeführt hat                        |
| Modul        | Tool (oder Modul), in dem die Aktion ausgeführt wurde                                                     |
| Gateway       | Name des Windows Admin Center-Gatewaycomputers, auf dem die Aktion ausgeführt wurde                     |
| Userongatder | Der Benutzername für den Zugriff auf das Windows Admin Center-Gateway und das Ausführen der Aktion.                    |
| Userontarget  | Der Benutzername, der für den Zugriff auf den verwalteten Zielserver verwendet wird, wenn er sich von userongatweg unterscheidet (d. h. der Benutzer, der mithilfe des Servers mit den Anmelde Informationen von "Verwalten |
| Delegierung    | Boolescher Wert: Wenn der verwaltete Zielserver das Gateway vertraut und Anmelde Informationen vom Client Computer des Benutzers delegiert werden.             |
| GEFAHREN          | Boolescher Wert: Wenn der Benutzer mithilfe von [runden](https://technet.microsoft.com/mt227395.aspx) Anmelde Informationen auf den Server zugegriffen hat                          |
| Datei          | Name der hochgeladenen Datei, wenn es sich bei der Aktion um einen Datei Upload handelt                                |

## <a name="learn-about-windows-admin-center-activity-with-event-logging"></a>Weitere Informationen zur Windows Admin Center-Aktivität mit Ereignisprotokollierung

Das Windows Admin Center protokolliert die gatewayaktivität im Ereignis Kanal auf dem Gatewaycomputer, damit Sie Probleme beheben und Metriken zur Verwendung anzeigen können. Diese Ereignisse werden im Ereignis Kanal **Microsoft-servermanagementexperience** protokolliert.

[Erfahren Sie mehr über die Problembehandlung in Windows Admin Center.](troubleshooting.md)
