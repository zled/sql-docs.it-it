---
title: Metodo setHostNameInCertificate (SQLServerDataSource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- setHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 84fe40795339ad4cc858716fbf73417363fb1673
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>Metodo setHostNameInCertificate (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il nome host da utilizzare per la convalida di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificato Secure Sockets Layer (SSL).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>Parametri  
 *hostNameInCertificate*  
  
 Oggetto **stringa** che contiene il nome host.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di hostNameInCertificate viene utilizzato per convalidare il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificato SSL quando il livello di comunicazione è crittografato tramite SSL. Il valore predefinito è null.  
  
 Se la proprietà hostNameInCertificate è impostata su null o non specificato, il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] utilizzerà il valore della proprietà serverName per la convalida di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] certificato SSL. Se la proprietà hostNameInCertificate è impostata su una stringa o una stringa vuota "", tale valore verrà utilizzato dal driver per la convalida del certificato SSL server.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
