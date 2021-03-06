---
ms.assetid: 606df285-259c-4c6b-8583-9aca1d614c43
title: Verwenden einer Anspruchsregel vom Typ "Weiterleiten" oder "Filtern"
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 49061aaab2f46d7d3abe80d4fade98c10654fc37
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407296"
---
# <a name="when-to-use-a-pass-through-or-filter-claim-rule"></a>Verwenden einer Anspruchsregel vom Typ "Weiterleiten" oder "Filtern"
Sie können diese Regel in Active Directory-Verbunddienste (AD FS) \(AD FS\) verwenden, wenn Sie einen bestimmten eingehenden Anspruchstyp verwenden und dann eine Aktion anwenden, die bestimmt, welche Ausgabe auf Basis der Werte im eingehenden Anspruch erfolgen soll. Wenn Sie diese Regel verwenden, werden Ansprüche weitergeleitet bzw. gefiltert, die der Regellogik in der folgenden Tabelle entsprechen. Dies geschieht auf Grundlage der Optionen, die Sie in der Regel konfigurieren.  
  
|Regeloption|Regellogik|  
|---------------|--------------|  
|Alle Anspruchswerte weiterleiten|Wenn der eingehende Anspruchstyp dem *angegebenen Anspruchstyp* und der Wert einem *beliebigen Wert* entspricht, den Anspruch weiterleiten|  
|Nur einen bestimmten Anspruchswert weiterleiten|Wenn der eingehende Anspruchstyp dem *angegebenen Anspruchstyp* und der Wert einem *angegebenen Anspruchswert* entspricht, den Anspruch weiterleiten|  
|Nur Anspruchs Werte weiterleiten, die einem bestimmten e\--Mail-suffixwert entsprechen|Wenn der eingehende Anspruchstyp dem *angegebenen Anspruchstyp* und der Wert einem *angegebenen Suffixwert* entspricht, den Anspruch weiterleiten|  
|Nur Anspruchswerte weiterleiten, die mit einem bestimmten Wert anfangen|Wenn der eingehende Anspruchstyp dem *angegebenen Anspruchstyp* und der Wert mit einem *angegebenen Anspruchswert* beginnt, den Anspruch weiterleiten|  
  
Die folgenden Abschnitte enthalten eine grundlegende Einführung in Anspruchsregeln und bieten weitere Details zur Verwendung dieser Regeln.  
  
## <a name="about-claim-rules"></a>Informationen zu Anspruchsregeln  
Eine Anspruchs Regel stellt eine Instanz der Geschäftslogik dar, die einen eingehenden Anspruch annimmt, eine Bedingung darauf \(anwendet, wenn x\) und y ist, und einen ausgehenden Anspruch basierend auf den Bedingungs Parametern erzeugt. Die folgende Liste enthält wichtige Tipps zu Anspruchsregeln, die Sie kennen sollten, bevor Sie fortfahren, dieses Thema zu lesen:  
  
-   Im Snap\--in "AD FS-Verwaltung" können Anspruchs Regeln nur mithilfe von Anspruchs Regel Vorlagen erstellt werden.  
  
-   Anspruchs Regeln verarbeiten eingehende Ansprüche entweder direkt von einem Anspruchs \(Anbieter (z. b.\) Active Directory oder einem anderen Verbunddienst oder von der Ausgabe der Akzeptanz Transformationsregeln für eine Anspruchs Anbieter-Vertrauensstellung.  
  
-   Anspruchsregeln werden vom Anspruchsausstellungsmodul chronologisch nach einem bestimmten Regelsatz verarbeitet. Indem Sie eine Rangfolge der Regeln festlegen, können Sie Ansprüche, die durch vorausgehende Regeln in einem bestimmten Regelsatz generiert werden, weiter optimieren oder filtern.  
  
-   Anspruchsregelvorlagen erfordern immer, dass Sie einen eingehenden Anspruchstyp angeben. Allerdings können Sie mehrere Anspruchswerte mit den gleichen Anspruchstyp mithilfe einer einzigen Regel verarbeiten.  
  
Ausführlichere Informationen zu Anspruchs Regeln und Anspruchs Regelsätzen finden Sie [unter Rolle der Anspruchs Regeln](The-Role-of-Claim-Rules.md). Weitere Informationen zur Verarbeitung von Regeln finden Sie [unter The Role of the Claims Engine](The-Role-of-the-Claims-Engine.md). Weitere Informationen zur Verarbeitung von Anspruchs Regelsätzen finden Sie [unter der Rolle der Anspruchs Pipeline](The-Role-of-the-Claims-Pipeline.md).  
  
## <a name="pass-through-all-claim-values"></a>Alle Anspruchswerte weiterleiten  
Wenn Sie diese Aktion verwenden, werden alle eingehenden Anspruchswerte für den angegebenen Anspruchstyp als ausgehende Ansprüche weitergeleitet. Wenn der Typ des eingehenden Anspruchs als Anspruchstyp "Rolle" angegeben wird, werden alle eingehenden Anspruchswerte z. B. einzeln in neue ausgehende Ansprüche mit dem ausgehenden Anspruchstyp "Rolle" kopiert.  
  
## <a name="filtering-a-claim"></a>Filtern eines Anspruchs  
In AD FS bedeutet der Begriff " *Anspruchs Filterung* " das Filtern oder einschränken eingehender Anspruchs Werte, sodass nur bestimmte Werte als ausgehende Ansprüche übermittelt oder gesendet werden. Diese Funktion wird durch die Regelvorlage **Eingehenden Anspruch weiterleiten oder filtern** ermöglicht. In den Eigenschaften der Regel können Sie Bedingungen festlegen, um eingehende Werte so zu filtern, dass nur die Werte weitergeleitet werden, die die angegebenen Kriterien erfüllen.  
  
Mithilfe dieser Regel können Sie z. B. nur Ansprüche weiterleiten, die dem Anspruchswert "Käufer" entsprechen, wenn der Typ des eingehenden Anspruchs dem Anspruchstyp "Rolle" entspricht. Sie können mit dieser Regel auch ausschließlich Ansprüche zum Namen des Benutzers, aber keine Ansprüche ausstellen, die die Sozialversicherungsnummer des Benutzers enthalten.  
  
Wenn Sie eine Filterbedingung mit dieser Regel verwenden, werden alle eingehenden Ansprüche untersucht, um zu bestimmen, welche Ansprüche den von der Regel festgelegten Kriterien entsprechen. Alle anderen Ansprüche werden ignoriert, sodass nur angegebene Anspruchswerte, die einem ausgewählten Anspruchstyp entsprechen, weitergeleitet werden.  
  
Wenn z. b. in der folgenden Abbildung gezeigt wird, dass eine Regel mit der Bedingung festgelegt wird, dass nur eingehende Ansprüche gefiltert werden, die an den UPN-Anspruchstyp und schließlich auf enden @fabrikam.com, werden alle anderen eingehenden Ansprüche ignoriert, es sei denn, Sie erfüllen diese Kriterien. Dies schließt den eingehenden Anspruch mit dem Anspruchstyp E\--Mail-Adresse ein, obwohl der Anspruchs @fabrikam.comWert in endet. In diesem Fall wird nur der Anspruch, der den Wert Nick@fabrikam.com von enthält, an die vertrauende Seite gesendet.  
  
![Verwendungsweise von Pass-Through](media/adfs2_filter.gif)  
  
## <a name="configuring-this-rule-on-a-claims-provider-trust"></a>Konfigurieren diese Regel in einer Anspruchsanbietervertrauensstellung  
Bei Verwendung einer Anspruchsanbieter-Vertrauensstellung kann diese Regel zum Weiterleiten von ausschließlich eingehenden Ansprüchen vom Anspruchsanbieter konfiguriert werden, die bestimmten Einschränkungen entsprechen. Angenommen, Sie möchten nur e\--Mail-Ansprüche vom Anspruchs Anbieter akzeptieren. Daher verwenden Sie diese Regel Vorlage, um e\--Mail-Anspruchs Typen zu akzeptieren, die mit dem Domain Name System \(DNSdesAnspruchsAnbietersenden.\) Name.  
  
## <a name="configuring-this-rule-on-a-relying-party-trust"></a>Konfigurieren diese Regel in einer Vertrauensstellung der vertrauenden Seite  
Wenn Sie eine Vertrauensstellung der vertrauenden Seite verwenden, kann diese Regel so konfiguriert werden, dass an die vertrauende Seite zu sendende ausgehende Ansprüche weitergeleitet oder gefiltert werden. Einige vertrauende Seiten können bestimmte Anspruchstypen ggf. nicht verstehen, oder bestimmte Ansprüche enthalten möglicherweise vertrauliche Informationen, der nicht an bestimmte vertrauende Seiten gesendet werden sollen. Diese Regelvorlage kann helfen, diese Richtlinien für eine bestimmte Vertrauensstellung der vertrauenden Seite zu erzwingen.  
  
## <a name="how-to-create-this-rule"></a>Erstellen dieser Regel  
Sie erstellen diese Regel entweder mithilfe der Anspruchs Regel Sprache oder mithilfe der Regel Vorlage zum Weiterleiten oder Filtern eingehender Ansprüche im Snap\--in "AD FS-Verwaltung". Diese Regelvorlage bietet die folgenden Konfigurationsoptionen:  
  
-   Anspruchsregelname angeben  
  
-   Angeben eines eingehenden Anspruchstyps  
  
-   Alle Anspruchswerte weiterleiten  
  
-   Nur einen bestimmten Anspruchswert weiterleiten  
  
-   Nur Anspruchs Werte weiterleiten, die einem bestimmten e\--Mail-suffixwert entsprechen  
  
-   Nur Anspruchswerte weiterleiten, die mit einem bestimmten Wert anfangen  
  
Weitere Anweisungen zum Erstellen dieser Vorlage finden Sie unter [Erstellen einer Regel zum Weiterleiten oder Filtern eines eingehenden Anspruchs](https://technet.microsoft.com/library/dd807060.aspx) im AD FS Bereitstellungs Handbuch.  
  
## <a name="using-the-claim-rule-language"></a>Verwenden der Anspruchsregelsprache  
Falls ein Anspruch nur gesendet werden soll, wenn der Wert des Anspruchs mit einem benutzerdefinierten Muster übereinstimmt, müssen Sie eine benutzerdefinierte Regel verwenden. Weitere Informationen finden Sie unter "Wann sollte eine benutzerdefinierte Anspruchsregel verwendet werden?".  
  
### <a name="examples-of-how-to-construct-a-pass-through-or-filter-rule-syntax"></a>Beispiele für das Erstellen der Syntax einer Weiterleitungs- oder Filterregel  
Eine einfache Filterregel filtert Ansprüche basierend auf einer der oben beschriebenen Eigenschaften. Beispielsweise werden mit der folgenden Regel alle e\--Mail-Ansprüche weitergeleitet:  
  
```  
c:[type == “http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress”]  => issue(claim  = c);  
```  
  
Filter können logisch und\-zusammengefasst werden. Die folgende Regel akzeptiert z. b. alle e\--Mail-Ansprüche mit dem Wert.johndoe@fabrikam.com:  
  
```  
c:[type == “http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress”, value == “johndoe@fabrikam.com “]  => issue(claim  = c);  
```  
  
In den obigen Beispielen wurde bei den Filtern stets ein Gleichheitsoperator verwendet. Die Anspruchsregelsprache unterstützt die folgenden Operatoren:  
  
-   \=\=groß-\-/Kleinschreibung \- \(\)  
  
-   \!\=ungleich Groß-/Kleinschreibung\-beachten \- \(\)  
  
-   \=~\-reguläre Ausdrucks Übereinstimmung  
  
-   \!~ \-nicht\-Übereinstimmung regulärer Ausdrücke  
  
Die folgende Regel akzeptiert z. b. alle e\--Mail-Ansprüche, die nicht vom lokalen Verbund Server ausgegeben werden und das Suffix Boeing.com aufweisen:  
  
```  
c:[type == “http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress”, value =~ “^.*@boeing\.com$” , issuer != “LOCAL AUTHORITY”]  => issue(claim  = c);  
```  
  
### <a name="best-practices-for-creating-custom-rules"></a>Bewährte Methoden zum Erstellen benutzerdefinierter Regeln  
Wie in der folgenden Tabelle beschrieben, kann ein Filter auf eine oder mehrere der Eigenschaften jedes Anspruchs angewendet werden.  
  

| Anspruchseigenschaft |                                                                                                                                                                                                                                                                                                                                                  Beschreibung                                                                                                                                                                                                                                                                                                                                                  |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Typ      |                                                                                                                                                                                        Der Anspruchstyp \(, der in der Regel\) als URI dargestellt wird, spiegelt eine implizite Vereinbarung zwischen Partnern in einem Verbund darüber wider, welche Art von Informationen im Anspruch übermittelt wird. Beispielsweise enthalten Ansprüche vom Typ http:\/\/Schemas.xmlsoap.org\/WS\/2005\/05\/Identity\/Claims\/EmailAddress das e\-e-Mail-Adresse des Benutzers.                                                                                                                                                                                         |
|     Wert      |                                                                                                                                                                                                                                                                   Der Wert des Anspruchs. Beispielsweise kann ein Anspruch des Typs "http\/:\/\/Schemas.xmlsoap.org\/WS\/2005\/05\/Identity\/Claims EmailAddress" den Wertjohndoe@fabrikam.com                                                                                                                                                                                                                                                                    |
|   ValueType    |                                                                                                                                                                                                  Der ValueType stellt dar, wie die Informationen, die im Wert des Anspruchs enthalten sind, interpretiert werden sollen. In der Regel wird ValueType auf http\/:\/www.w3.org\/2001\/XmlSchema\#String festgelegt, aber der Anspruchs Wert kann Base64Binary-codierte Daten \(enthalten, z. b. ein Bild. \) oder ein Datum, ein boolescher Wert usw.                                                                                                                                                                                                  |
|     Aussteller     | "Issuer" ist der Aussteller, der zuletzt die Ansprüche zum Benutzer ausgestellt hat. Wenn die Ansprüche vom Verbundserver eines Anspruchsanbieters bezogen werden, wird der Aussteller aller Ansprüche auf "LOCAL AUTHORITY" festgelegt. Wenn die Ansprüche vom Verbundserver eines Verbundanbieters empfangen wurden, wird der Aussteller der Ansprüche auf die Anspruchsanbieter-ID des Anspruchsanbieters festgelegt, der das Token signiert hat. Wenn anschließend Regeln für Ansprüche verarbeitet werden, die von einem Anspruchsanbieter empfangen wurden, wird der Aussteller der Ansprüche auf denselben Wert festgelegt. Bei der Erstellung von Regeln für eine vertrauende Seite kann die "Issuer"-Eigenschaft verwendet werden, um zwischen Ansprüchen zu unterscheiden, die von verschiedenen Anspruchsanbietern stammen. |
| OriginalIssuer |                                                                                                   Diese Anspruchseigenschaft dient zum Angeben, von welchem Verbundserver der Anspruch ursprünglich ausgestellt wurde. Da die Eigenschaft Aussteller der Ansprüche auf den letzten Verbund Server festgelegt ist, der das Token signiert hat, ist der ursprüngliche Aussteller in Szenarios nützlich, in denen ein Anspruch durch mehr \(als einen Verbund Server fließt, z. b. eine vertrauende Seite, die ein Token empfängt. der Verbund Server eines Verbund Anbieters ist möglicherweise interessiert, welcher bestimmte Anspruchs Anbieter-Verbund Server den Benutzer authentifiziert hat.\)                                                                                                   |
|   Eigenschaften   |                                                                                                                             Neben den oben beschriebenen fünf Eigenschaften hat jeder Anspruch auch einen Eigenschaftenbehälter, in dem benannte Eigenschaften gespeichert werden können. Diese Eigenschaften werden nicht im Token serialisiert und sind nur sinnvoll für die Übergabe von Informationen zwischen Komponenten der Anspruchsausstellungs-Pipeline innerhalb des Zuständigkeitsbereichs eines einzelnen Verbundservers. Beispiel: Festlegen einer Eigenschaft während der Verarbeitung von Anspruchsanbieterregeln und das anschließende Verweisen darauf in den Regeln der vertrauenden Seite.                                                                                                                              |

