---
title: Aufheben der Registrierung eines NPS aus einer Active Directory-Domäne
description: Sie können dieses Thema verwenden, um einen Server, auf dem der Netzwerk Richtlinien Server ausgeführt wird, in Windows Server 2016 in der NPS-Standard Domäne oder in einer anderen Domäne zu registrieren.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 68a94616-3c29-45bd-bd33-e4c578f119e1
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 3225c42ab14e2ea1bc283f520b14c09ebc2254c4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396080"
---
# <a name="unregister-an-nps-from-an-active-directory-domain"></a>Aufheben der Registrierung eines NPS aus einer Active Directory-Domäne

>Gilt für: Windows Server (halbjährlicher Kanal), Windows Server 2016

Beim Verwalten der NPS-Bereitstellung ist es möglicherweise hilfreich, eine NPS in eine andere Domäne zu verschieben, ein NPS zu ersetzen oder ein NPS außer Kraft zu setzen. 

Wenn Sie ein NPS verschieben oder außer Betrieb nehmen, können Sie die Registrierung des NPS in den Active Directory Domänen aufheben, in denen das NPS über die Berechtigung zum Lesen der Eigenschaften von Benutzerkonten in Active Directory verfügt.

Sie müssen mindestens Mitglied der Gruppe **Administratoren** oder einer entsprechenden Gruppe sein, um diese Verfahren ausführen zu können.

## <a name="to-unregister-an-nps"></a>So heben Sie die Registrierung eines NPS auf

1. Klicken Sie auf dem Domänen Controller in Server-Manager auf **Extras, und klicken Sie dann**auf **Active Directory Benutzer und Computer**. Die Konsole Active Directory-Benutzer und -Computer wird geöffnet.

2. Klicken Sie auf **Benutzer**, und doppelklicken Sie dann auf **RAS-und IAS-Server**.

3. Klicken Sie auf die Registerkarte **Mitglieder** , und wählen Sie dann den NPS aus, dessen Registrierung Sie aufheben möchten.

4. Klicken Sie auf **Entfernen**, klicken Sie auf **Ja**und dann auf **OK**.

