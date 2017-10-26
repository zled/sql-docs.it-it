---
title: Metodo setFailoverPartner (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.setFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 256c8da2fa3fd814057f7d81c4d1b0840c8b6919
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
  
  

