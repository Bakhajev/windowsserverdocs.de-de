---
ms.assetid: 475e34f9-9399-43f4-a840-9dd77258e11a
title: Erstellen einer Regel zum Senden der Gruppenmitgliedschaft als Anspruch
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: b8217302cc0ec5bc6972004cb2f26ffae1371614
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407580"
---
# <a name="create-a-rule-to-send-group-membership-as-a-claim"></a>Erstellen einer Regel zum Senden der Gruppenmitgliedschaft als Anspruch

Mithilfe der Regel Vorlage "Send Group Membership as a Claim" \(in\)Active Directory-Verbunddienste (AD FS) AD FS können Sie eine Regel erstellen, die es Ihnen ermöglicht, eine Active Directory Sicherheitsgruppe auszuwählen, die als Anspruch gesendet werden soll. Von dieser Regel wird nur ein einzelner Anspruch auf Grundlage der ausgewählten Gruppe ausgegeben. Beispielsweise können Sie diese Regel Vorlage verwenden, um eine Regel zu erstellen, die einen Gruppen Anspruch mit dem Wert "admin" sendet, wenn der Benutzer Mitglied der Sicherheitsgruppe "Domänen-Admins" ist. Diese Regel sollte nur für Benutzer in der lokalen Active Directory Domäne verwendet werden.  
  
Mithilfe des folgenden Verfahrens können Sie eine Anspruchs Regel mit dem Snap\--in "AD FS-Verwaltung" erstellen.  
  
Sie müssen mindestens Mitglied der Gruppe **Administratoren** oder einer entsprechenden Gruppe auf dem lokalen Computer sein, um dieses Verfahren ausführen zu können.  Ausführliche Informationen zur Verwendung der entsprechenden Konten und Gruppenmitgliedschaften finden Sie unter [lokale und Domänen Standard Gruppen](https://go.microsoft.com/fwlink/?LinkId=83477).   

## <a name="to-create-a-rule-to-send-group-membership-as-a-claim-on-a-relying-party-trust-in-windows-server-2016"></a>So erstellen Sie eine Regel zum Senden der Gruppenmitgliedschaft als Anspruch auf eine Vertrauensstellung der vertrauenden Seite in Windows Server 2016 

1.  Klicken Sie in Server-Manager **auf Extras**, und wählen Sie dann **AD FS Verwaltung**aus.  
  
2.  Klicken Sie in der Konsolen Struktur unter **AD FS**auf Vertrauens Stellungen der vertrauenden **Seite**. 
![Regel erstellen](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG)  
  
3.  Klicken\-Sie mit der rechten Maustaste auf die ausgewählte Vertrauensstellung, und klicken Sie dann auf **Richtlinie**zum
![Regel erstellen](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule10.PNG)   
  
4.  Klicken Sie im Dialogfeld **Richtlinie für Anspruchs Ausstellung bearbeiten** unter Ausstellungs **Transformationsregeln** auf **Regel hinzufügen** , um den Regel-Assistenten zu starten. 
![Regel erstellen](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule11.PNG)    

5.  Wählen Sie auf der Seite **Regel Vorlage auswählen** unter **Anspruchs Regel Vorlage**die Option **Gruppenmitgliedschaft als Anspruch senden** aus der Liste aus, und klicken Sie dann auf **weiter**.  
![Regel erstellen](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group3.PNG)      

6.   Geben Sie auf der Seite **Regel konfigurieren** unter **Anspruchs Regel Name** den anzeigen Amen für diese Regel ein, klicken Sie in der **Gruppe des Benutzers** auf **Durchsuchen** , und wählen Sie eine Gruppe aus, und wählen Sie unter **Typ des ausgehenden Anspruchs den gewünschten Anspruchstyp** und dann unter  **Typ des ausgehenden Anspruchs** geben Sie einen Wert ein.
![Regel erstellen](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group4.PNG)   

7.  Klicken Sie auf **Fertig** stellen.  
  
8.  Klicken Sie im Dialogfeld **Anspruchs Regeln bearbeiten** auf **OK** , um die Regel zu speichern.
  
## <a name="to-create-a-rule-to-send-group-membership-as-a-claim-on-a-claims-provider-trust-in-windows-server-2016"></a>So erstellen Sie eine Regel zum Senden der Gruppenmitgliedschaft als Anspruch auf eine Anspruchs Anbieter-Vertrauensstellung in Windows Server 2016 
  
1.  Klicken Sie in Server-Manager **auf Extras**, und wählen Sie dann **AD FS Verwaltung**aus.  
  
2.  Klicken Sie in der Konsolen Struktur unter **AD FS**auf **Anspruchs Anbieter**-Vertrauens Stellungen. 
![Regel erstellen](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule1.PNG)  
  
3.  Klicken\-Sie mit der rechten Maustaste auf die ausgewählte Vertrauensstellung und dann auf **Anspruchs Regeln bearbeiten**.
![Regel erstellen](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule2.PNG)   
  
4.  Klicken Sie im Dialogfeld **Anspruchs Regeln bearbeiten** unter **Akzeptanz Transformationsregeln** auf **Regel hinzufügen** , um den Regel-Assistenten zu starten.
![Regel erstellen](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule3.PNG)    

5.  Wählen Sie auf der Seite **Regel Vorlage auswählen** unter **Anspruchs Regel Vorlage**die Option **Gruppenmitgliedschaft als Anspruch senden** aus der Liste aus, und klicken Sie dann auf **weiter**.  
![Regel erstellen](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group3.PNG)     

6.   Geben Sie auf der Seite **Regel konfigurieren** unter **Anspruchs Regel Name** den anzeigen Amen für diese Regel ein, klicken Sie in der **Gruppe des Benutzers** auf **Durchsuchen** , und wählen Sie eine Gruppe aus, und wählen Sie unter **Typ des ausgehenden Anspruchs den gewünschten Anspruchstyp** und dann unter  **Typ des ausgehenden Anspruchs** geben Sie einen Wert ein. 
![Regel erstellen](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group4.PNG)      

7.  Klicken Sie auf **Fertig** stellen.  
  
8.  Klicken Sie im Dialogfeld **Anspruchs Regeln bearbeiten** auf **OK** , um die Regel zu speichern.  




  
## <a name="to-create-a-rule-to-send-group-membership-as-a-claim-in-windows-server-2012-r2"></a>So erstellen Sie eine Regel zum Senden der Gruppenmitgliedschaft als Anspruch in Windows Server 2012 R2 
  
1.  Klicken Sie in Server-Manager **auf Extras**, und wählen Sie dann **AD FS Verwaltung**aus.  
  
2.  Klicken Sie in der Konsolen Struktur **unter\\AD FS Vertrauens**Stellungen entweder auf **Anspruchs Anbieter** -Vertrauens Stellungen oder Vertrauens Stellungen der vertrauenden **Seite**, und klicken Sie dann auf eine bestimmte Vertrauensstellung in der Liste, in der Sie diese Regel erstellen möchten.  
  
3.  Klicken\-Sie mit der rechten Maustaste auf die ausgewählte Vertrauensstellung und dann auf **Anspruchs Regeln bearbeiten**.
![Regel erstellen](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule6.PNG)  
  
4.  Wählen Sie im Dialogfeld **Anspruchs Regeln bearbeiten** je nach der zu bearbeitenden Vertrauensstellung und dem Regelsatz, in dem Sie diese Regel erstellen möchten, eine der folgenden Registerkarten aus, und klicken Sie dann auf **Regel hinzufügen** , um den Regel-Assistenten zu starten, der diesem Regelsatz zugeordnet ist. :  
  
    -   **Akzeptanz Transformationsregeln**  
  
    -   **Ausstellungs Transformationsregeln**  
  
    -   **Ausstellungs Autorisierungs Regeln**  
  
    -   **Delegierungs Autorisierungs Regeln**  
![Regel erstellen](media/Create-a-Rule-to-Permit-All-Users/permitall5.PNG)
    
5.  Wählen Sie auf der Seite **Regel Vorlage auswählen** unter **Anspruchs Regel Vorlage**die Option **Gruppenmitgliedschaft als Anspruch senden** aus der Liste aus, und klicken Sie dann auf **weiter**.  
![Regel erstellen](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group1.PNG)

6.  Geben Sie auf der Seite **Regel konfigurieren** unter **Anspruchs Regel Name** den anzeigen Amen für diese Regel ein, klicken Sie in der **Gruppe des Benutzers** auf **Durchsuchen** , und wählen Sie eine Gruppe aus, und wählen Sie unter **Typ des ausgehenden Anspruchs den gewünschten Anspruchstyp** und dann unter  **Typ des ausgehenden Anspruchs** geben Sie einen Wert ein.  
![Regel erstellen](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group2.PNG)  

7.  Klicken Sie auf **Fertig stellen**.  
  
8.  Klicken Sie im Dialogfeld **Anspruchs Regeln bearbeiten** auf **OK** , um die Regel zu speichern.  



## <a name="additional-references"></a>Weitere Verweise 
[Konfigurieren von Anspruchsregeln](Configure-Claim-Rules.md)  
 
[Prüfliste: Erstellen von Anspruchsregeln für eine Vertrauensstellung der vertrauenden Seite](https://technet.microsoft.com/library/ee913578.aspx)  

[Prüfliste: Erstellen von Anspruchsregeln für eine Anspruchsanbieter-Vertrauensstellung](https://technet.microsoft.com/library/ee913564.aspx)  
  
[Wann sollte eine Autorisierungs Anspruchs Regel verwendet werden?](../../ad-fs/technical-reference/When-to-Use-an-Authorization-Claim-Rule.md)  

[Rolle von Ansprüchen](../../ad-fs/technical-reference/The-Role-of-Claims.md)  
  
[Rolle von Anspruchsregeln](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md) 
