---
title: Migrieren des AD FS 2,0-Verbund Proxyservers
description: Bietet Informationen zum Migrieren eines AD FS Proxy Servers zu Windows Server 2012 R2.
author: billmath
ms.author: billmath
manager: femila
ms.date: 07/10/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 57367cadd3c7ce3d031c6eb3a53c333422543dae
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359371"
---
# <a name="migrate-the-active-directory-federation-services-proxy-server-to-windows-server-2012-r2"></a>Migrieren des Active Directory-Verbunddienste (AD FS) Proxy Servers zu Windows Server 2012 R2

In Active Directory-Verbunddienste (AD FS) (AD FS) in Windows Server 2012 R2 wird die Rolle eines Verbund Server Proxys von einem neuen Remote Zugriffs Rollen Dienst namens webanwendungsproxy behandelt. Wenn Sie in Windows Server 2012 R2 ihren AD FS für die Barrierefreiheit von außerhalb des Unternehmensnetzwerks aktivieren möchten, können Sie einen oder mehrere webanwendungsproxys bereitstellen. Es ist jedoch nicht möglich, einen Verbund Server Proxy unter Windows Server 2008 R2 oder Windows Server 2012 zu einem webanwendungsproxy zu migrieren, der unter Windows Server 2012 R2 ausgeführt wird.  
  
> [!IMPORTANT]
>  Die Migration eines Verbund Server Proxys unter Windows Server 2008, Windows Server 2008 R2 oder Windows Server 2012 zu einem webanwendungsproxy, der unter Windows Server 2012 R2 ausgeführt wird, wird nicht unterstützt.  
  
Wenn Sie AD FS in einer migrierten Windows Server 2012 R2-Farm für den Extranetzugriff konfigurieren möchten, müssen Sie eine neue Bereitstellung von einem oder mehreren webanwendungsproxy-Computern als Teil Ihrer AD FS-Infrastruktur ausführen.  
  
Wenn Sie die Bereitstellung eines Webanwendungsproxys planen, lesen Sie die Informationen in den folgenden Themen:  
  
- [Planen der webanwendungsproxy-Infrastruktur](https://technet.microsoft.com/library/dn383648.aspx)  
  
- [Planen des webanwendungsproxy-Servers](https://technet.microsoft.com/library/dn383647.aspx)  
  
  Sie können zum Bereitstellen eines Webanwendungsproxys die Schritte in den folgenden Themen ausführen:  
  
- [Konfigurieren der webanwendungsproxy-Infrastruktur](https://technet.microsoft.com/library/dn383644.aspx)  
  
- [Installieren und Konfigurieren des webanwendungsproxy-Servers](https://technet.microsoft.com/library/dn383662.aspx)  
  
## <a name="next-steps"></a>Nächste Schritte
 [Migrieren Active Directory-Verbunddienste (AD FS) Rollen Dienste zu Windows Server 2012 R2](migrate-ad-fs-service-role-to-windows-server-r2.md)   
 [Vorbereiten der Migration des AD FS Verbund Servers](prepare-migrate-ad-fs-server-r2.md)   
 [Migrieren des AD FS Verbund Servers](migrate-ad-fs-fed-server-r2.md)    
 [Überprüfen der AD FS Migration zu Windows Server 2012 R2](verify-ad-fs-migration.md)

