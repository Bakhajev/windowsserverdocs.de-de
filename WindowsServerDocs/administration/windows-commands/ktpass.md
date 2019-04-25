---
title: ktpass
description: 'Windows-Befehle Thema ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 47087676-311e-41f1-8414-199740d01444
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7a865b94bbbf2245e8a2e07638064f66de920b90
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59886671"
---
# <a name="ktpass"></a>ktpass

>Gilt für: WindowsServer (Halbjährlicher Kanal), Windows Server 2016, Windows Server 2012 R2, WindowsServer 2012

Konfiguriert den Dienstprinzipalnamen für den Host oder Dienst in active Directory-Domänendienste (AD DS) und generiert eine keytab-Datei, die den gemeinsamen geheimen Schlüssel des Diensts enthält. Die KEYTAB-Datei basiert auf der Massachusetts Institute of Technology (MIT)-Implementierung des Kerberos-Authentifizierungsprotokolls. Das Befehlszeilentool Ktpass kann nicht-Windows-Dienste, die durch den Dienst des Kerberos-Schlüsselverteilungscenter (Key Distribution Center, KDC) bereitgestellten Interoperabilitätsfunktionen verwenden Kerberos-Authentifizierung unterstützen. Dieses Thema gilt für die Betriebssystemversionen, die festgelegt werden, der **gilt für** Liste am Anfang des Themas.  
  
## <a name="syntax"></a>Syntax  
```  
ktpass  
[/out <FileName>]   
[/princ <PrincipalName>]   
[/mapuser <UserAccount>]   
[/mapop {add|set}] [{-|+}desonly] [/in <FileName>]  
[/pass {Password|*|{-|+}rndpass}]  
[/minpass]  
[/maxpass]  
[/crypto {DES-CBC-CRC|DES-CBC-MD5|RC4-HMAC-NT|AES256-SHA1|AES128-SHA1|All}]  
[/itercount]  
[/ptype {KRB5_NT_PRINCIPAL|KRB5_NT_SRV_INST|KRB5_NT_SRV_HST}]  
[/kvno <KeyversionNum>]  
[/answer {-|+}]  
[/target]  
[/rawsalt] [{-|+}dumpsalt] [{-|+}setupn] [{-|+}setpass <Password>]  [/?|/h|/help]  
```  
## <a name="parameters"></a>Parameter  
|Parameter|Beschreibung|  
|-------|--------|  
|/ Out <FileName>|Gibt den Namen, der die Kerberos Version 5 Keytab-Datei zu generieren. **Hinweis**: Dies ist die Keytab-Datei, die Sie übertragen auf einen Computer, der nicht das Windows-Betriebssystem ausgeführt wird, und klicken Sie dann ersetzen oder Zusammenführen mit Ihrer vorhandenen Keytab-Datei, /Etc/Krb5.keytab.|  
|/princ <PrincipalName>|Gibt den Prinzipalnamen in der Form host/computer.contoso.com@CONTOSO.COM. **Warnung:** Dieser Parameter ist Groß-/Kleinschreibung beachtet. Finden Sie unter ["Hinweise"](#BKMK_remarks) für Weitere Informationen.|  
|/mapuser <UserAccount>|Ordnet den Namen der Kerberos-Prinzipal, der durch angegeben ist die **Princ** Parameter, um das angegebene Domänenkonto.|  
|/mapop {hinzufügen&#124;festgelegt}|Gibt an, wie das Mapping-Attribut festgelegt ist.<br /><br />-   **Hinzufügen** fügt den Wert des angegebenen lokalen Benutzer namens hinzu. Dies ist der Standardwert.<br />-   **Legen Sie** legt den Wert für die standardmäßige DES (Data Encryption) – nur Verschlüsselung für den angegebenen lokalen Benutzernamen ein.|  
|{-&#124;+}desonly|Nur-DES-Verschlüsselung ist standardmäßig festgelegt.<br /><br />-   **+** Legt ein Konto für die nur-DES-Verschlüsselung.<br />-   **-** Gibt die Einschränkungen im Hinblick auf ein Konto für die nur-DES-Verschlüsselung frei. **WICHTIG:** Ab Windows 7 und Windows Server 2008 R2, unterstützt Windows nicht DES standardmäßig.|  
|/in <FileName>|Gibt die Keytab-Datei von einem Hostcomputer zu lesen, die nicht die Windows-Betriebssystem ausgeführt wird.|  
|/ pass {Kennwort&#124;*&#124;{-&#124;+} Rndpass}|Gibt ein Kennwort für den Prinzipal Benutzernamen, die angegeben wird die **Princ** Parameter. Mit "*" zur Kennworteingabe aufgefordert.|  
|/minpass|Legt die minimale Länge der zufälliges Kennwort und 15 Zeichen fest.|  
|/maxpass|Legt die maximale Länge des zufälliges Kennwort auf 256 Zeichen fest.|  
|/crypto {DES-CBC-CRC&#124;DES-CBC-MD5&#124;RC4-HMAC-NT&#124;AES256-SHA1&#124;AES128-SHA1&#124;All}|Gibt an, die Schlüssel, die in der Datei keytab-Datei generiert werden:<br /><br />-   **DES-CBC-CRC** Kompatibilität.<br />-   **DES-CBC-MD5** genauer auf die Implementierung MIT entspricht, und für Kompatibilität verwendet wird.<br />-   **RC4-HMAC-NT** 128-Bit-Verschlüsselung verwendet.<br />-   **AES256-SHA1** AES256-CTS-HMAC-SHA1-96-Verschlüsselung verwendet.<br />-   **SHA1-aes128** AES128-CTS-HMAC-SHA1-96-Verschlüsselung verwendet.<br />-   **Alle** Zustände an, dass alle kryptografischen Typen unterstützt, können verwendet werden. **Hinweis**: Die Standardeinstellungen basieren auf einer älteren MIT. Aus diesem Grund `/crypto` muss immer angegeben werden.|  
|/itercount|Gibt die Anzahl der Iterationen, die für die AES-Verschlüsselung verwendet wird. Der Standardwert ist, die **Itercount** für nicht-AES-Verschlüsselung ignoriert und auf 4.096 für die AES-Verschlüsselung festgelegt ist.|  
|/ptype {KRB5_NT_PRINCIPAL&#124;KRB5_NT_SRV_INST&#124;KRB5_NT_SRV_HST}|Gibt den Prinzipal an.<br /><br />-   **KRB5_NT_PRINCIPAL** ist der allgemeine Prinzipaltyp (empfohlen).<br />-   **KRB5_NT_SRV_INST** ist der Benutzer-Dienstinstanz.<br />-   **KRB5_NT_SRV_HST** ist die Hostinstanz für den Dienst.|  
|/kvno <KeyversionNum>|Gibt die Anzahl der Version des Schlüssels. Der Standardwert ist 1.|  
|und Antworten {-&#124;+}|Legt den Hintergrundmodus für die Antwort fest:<br /><br />**-** Antworten Zurücksetzen der Kennwörter eingegeben werden müssen, automatisch mit Nein.<br /><br />**+** Antworten zurücksetzen Kennwörter eingegeben werden müssen, automatisch mit "Ja".|  
|/ target|Legt fest, welcher Domänencontroller verwenden. Der Standardwert ist für den Domänencontroller erkannt werden, basierend auf den Benutzerprinzipalnamen. Wenn der Name des Domänencontrollers nicht behoben wird, fordert ein Dialogfeld, das einen gültigen Domänencontroller.|  
|/rawsalt|Erzwingt, dass Ktpass Rawsalt Algorithmus beim Generieren des Schlüssels zu verwenden. Dieser Parameter ist nicht erforderlich.|  
|{-&#124;+}dumpsalt|Die Ausgabe dieses Parameters wird gezeigt, die MIT salt-Algorithmus, der zum Generieren des Schlüssels verwendet wird.|  
|{-&#124;+}setupn|Legt fest, der Benutzerprinzipalname (UPN), zusätzlich zu den Dienstprinzipalnamen (SPN). Standardmäßig werden beide in die Keytab-Datei festgelegt.|  
|{-&#124;+}setpass <Password>|Legt fest, das Kennwort des Benutzers, wenn angegeben. Wenn Rndpass verwendet wird, wird stattdessen ein zufälliges Kennwort generiert.|  
|/?&#124;/h&#124;/help|Zeigt die Befehlszeilenhilfe für Ktpass helfen.|  
## <a name="BKMK_remarks"></a>"Hinweise"  
Dienste, die auf Systemen, auf denen das Windows-Betriebssystem ausgeführt, können mit Instanz-Dienstkonten in active Directory-Domänendiensten konfiguriert werden. Dadurch werden alle Kerberos-Client die Authentifizierung für Dienste, die nicht das Windows-Betriebssystem ausgeführt werden, mithilfe der Windows-KDCs.  
Die /princ-Parameter wird vom Ktpass nicht ausgewertet, und es wird verwendet, wie angegeben. Es erfolgt keine Überprüfung, um festzustellen, ob der Parameter, die exakte Groß-/Kleinschreibung entspricht der **"userPrincipalName"** Attributwert, wenn die Keytab-Datei generiert wird. Groß-/ Kleinschreibung Kerberos-Verteilungen, die Verwendung dieser Datei keytab-Datei treten möglicherweise Probleme beim liegt keine genaue Übereinstimmung für die Groß-/Kleinschreibung und kann bei der Vorauthentifizierung fehlschlagen. Überprüfen und rufen Sie die richtige **"userPrincipalName"** -Attributwert aus einer Exportdatei LDifDE. Zum Beispiel:  
```  
ldifde /f keytab_user.ldf /d "CN=Keytab User,OU=UserAccounts,DC=contoso,DC=corp,DC=microsoft,DC=com" /p base /l samaccountname,userprincipalname  
```  
## <a name="BKMK_examples"></a>Beispiele für  
Das folgende Beispiel veranschaulicht, wie Sie eine Kerberos-Keytab-Datei, machine.keytab, im aktuellen Verzeichnis für den Benutzer Sample1 zu erstellen. (Sie zusammenführen werden, diese Datei mit der Krb5.keytab-Datei auf einem Hostcomputer, die nicht die Windows-Betriebssystem ausgeführt wird.) Die Kerberos-Keytab-Datei wird für alle unterstützten Verschlüsselungstypen für den allgemeinen Prinzipaltyp erstellt werden.  
Um eine keytab-Datei für einen Hostcomputer zu generieren, die nicht die Windows-Betriebssystem ausgeführt wird, verwenden Sie die folgenden Schritte aus, um den Prinzipal mit dem Konto zuordnen, und legen Sie das Kennwort des Host-dienstprinzipals:  
1.  Verwenden Sie die active Directory-Benutzer und Computer-Snap-in auf ein Benutzerkonto für einen Dienst auf einem Computer zu erstellen, die nicht die Windows-Betriebssystem ausgeführt wird. Erstellen Sie z. B. ein Konto, mit dem Namen Sample1.  
2.  Verwenden Sie Ktpass, um eine identitätszuordnung für das Benutzerkonto einrichten, indem Sie Sie an einer Eingabeaufforderung Folgendes eingeben:  
    ```  
    ktpass /princ host/Sample1.contoso.com@CONTOSO.COM /mapuser Sample1 /pass MyPas$w0rd /out Sample1.keytab /crypto all /ptype KRB5_NT_PRINCIPAL /mapop set   
    ```  
    
    > [!NOTE]  
    > Sie können nicht mehrere Dienstinstanzen mit dem gleichen Benutzerkonto zuordnen.  
    
3.  Führen Sie die Keytab-Datei mit der /Etc/Krb5.keytab-Datei auf einem Hostcomputer, der nicht die Windows-Betriebssystem ausgeführt wird. 

#### <a name="additional-references"></a>Zusätzliche Referenzen  
[Befehlszeilensyntax](command-line-syntax-key.md)  