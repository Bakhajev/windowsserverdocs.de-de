---
title: AD-Gesamtstruktur Wiederherstellung-nicht autoritative Wiederherstellung
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: e4ce1d18-d346-492a-8bca-f85513aa3ac1
ms.technology: identity-adds
ms.openlocfilehash: d7792cd739931d758125c8946606beb043ce19dd
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71369091"
---
# <a name="performing-a-nonauthoritative-restore-of-active-directory-domain-services"></a>Ausführen einer nicht autoritativen Wiederherstellung von Active Directory Domain Services 

>Gilt für: Windows Server 2016, Windows Server 2012 und 2012 R2, Windows Server 2008 und 2008 R2

Führen Sie das folgende Verfahren aus, um eine nicht autoritative Wiederherstellung durchzuführen.  
  
In den folgenden Verfahren wird Wbadmin. exe verwendet, um eine nicht autoritative Wiederherstellung von Active Directory oder Active Directory Domain Services (AD DS) auszuführen. Wenn Sie eine andere Sicherungs Lösung verwenden oder wenn Sie beabsichtigen, die autoritative Wiederherstellung von SYSVOL später im Wiederherstellungsprozess der Gesamtstruktur abzuschließen, können Sie eine autoritative Wiederherstellung von SYSVOL mithilfe der folgenden alternativen Methoden ausführen:  
  
- Wenn Sie den Datei Replikations Dienst (File Replication Service, FRS) zum Replizieren von SYSVOL verwenden, befolgen Sie die Schritte im [Artikel 290762](https://go.microsoft.com/fwlink/?LinkId=148443) in der Microsoft Knowledge Base. verwenden Sie dazu den **BurFlags** -Registrierungsschlüssel, um FRS-Replikat 315457 [Gruppen erneut zu initialisieren 315457](https://support.microsoft.com/kb/315457)zum erneuten Erstellen der SYSVOL-Struktur. Um zu ermitteln, ob SYSVOL von FRS repliziert wird, finden Sie unter [bestimmen, ob der SYSVOL-Ordner eines Domänen Controllers von DFSR oder FRS repliziert wird](https://msdn.microsoft.com/library/windows/desktop/cc507518.aspx#determining_whether_a_domain_controller_s_sysvol_folder_is_replicated_by_dfsr_or_frs).  
- Wenn Sie die Replikation von SYSVOL mithilfe der DFS-Replikation (verteiltes Dateisystem) replizieren, finden Sie unter [Ausführen einer autorisierenden Synchronisierung von DFSR-replizierten SYSVOL](AD-Forest-Recovery-Authoritative-Recovery-SYSVOL.md)  

## <a name="performing-a-nonauthoritative-restore"></a>Ausführen einer nicht autorisierenden Wiederherstellung

Verwenden Sie das folgende Verfahren, um eine nicht autoritative Wiederherstellung von AD DS und eine autoritative Wiederherstellung von SYSVOL gleichzeitig durchzuführen, indem Sie Wbadmin. exe auf einem Domänen Controller mit Windows Server 2012, Windows Server 2008 R2 oder Windows Server 2008 verwenden. Die Sicherung muss explizit Systemstatus Daten einschließen. eine vollständige Server Sicherung, die für die vollständige Server Wiederherstellung verwendet wird, funktioniert nicht. Weitere Informationen zum Erstellen einer Systemstatus Sicherung finden Sie unter [Sichern der Systemstatus Daten](AD-Forest-Recovery-Backing-up-System-State.md).  
  
### <a name="to-perform-a-nonauthoritative-restore-of-ad-ds-and-authoritative-restore-of-sysvol-using-wbadminexe"></a>So führen Sie eine nicht autoritative Wiederherstellung AD DS und autoritative Wiederherstellung von SYSVOL mithilfe von "Wbadmin. exe" aus  
  
- Schließen Sie den Schalter **-authsysvol** in den Wiederherstellungs Befehl ein, wie im folgenden Beispiel gezeigt:  

   ```  
   wbadmin start systemstaterecovery <otheroptions> -authsysvol  
   ```  

   Zum Beispiel:  

   ```  
   wbadmin start systemstaterecovery -version:11/20/2012-13:00 -authsysvol  
   ```  
  
![Wiederherstellen](media/AD-Forest-Recovery-Nonauthoritative-Restore/nonauth.png)

## <a name="next-steps"></a>Nächste Schritte

- [Wiederherstellung der AD-Gesamtstruktur: Leitfaden](AD-Forest-Recovery-Guide.md)
- [Wiederherstellung der AD-Gesamtstruktur: Verfahren](AD-Forest-Recovery-Procedures.md)
