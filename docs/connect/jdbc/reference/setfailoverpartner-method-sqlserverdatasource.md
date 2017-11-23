---
title: Metodo setFailoverPartner (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDataSource.setFailoverPartner
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7aa59563e6980ef29f3e53e19519b83bcac8d721
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>Metodo setFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il nome del server di failover utilizzato nella configurazione del mirroring del database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *serverName*  
  
 Oggetto **stringa** che contiene il nome del server di failover.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore impostato da questo metodo viene utilizzato nel caso di un errore di connessione iniziale al server principale. Dopo avere effettuato la connessione iniziale, questo valore viene ignorato. Il [setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md) metodo deve anche essere utilizzato in combinazione con questo metodo oppure verrà generata un'eccezione.  
  
 Il driver non supporta la specifica del numero di porta del server di failover quando tale server viene impostato. Tuttavia, la chiamata di [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md) (metodo) e [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md) metodo con il [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) metodo è supportato.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
