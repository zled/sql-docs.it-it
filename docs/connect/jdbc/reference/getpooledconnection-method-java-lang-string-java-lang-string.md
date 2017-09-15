---
title: Metodo (lang. String, lang) getPooledConnection | Documenti Microsoft
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
- SQLServerConnectionPoolDataSource.getPooledConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f2e6391d-9aaf-4b09-ae1c-a27c1ada6301
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c62f975b9d9176941906f3ab8b5e5d7d241d14ff
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getpooledconnection-method-javalangstring-javalangstring"></a>Metodo getPooledConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tenta di stabilire una connessione di database fisica che possa essere utilizzata come connessione in pool in base al nome utente e alla password specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public javax.sql.PooledConnection getPooledConnection(java.lang.String user,  
                                                      java.lang.String password)  
```  
  
#### <a name="parameters"></a>Parametri  
 *utente*  
  
 Oggetto **stringa** che contiene il nome utente.  
  
 *passwword*  
  
 Oggetto **stringa** che contiene la password.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getPooledConnection viene specificato dal metodo nell'interfaccia javax.SQL. ConnectionPoolDataSource getPooledConnection.  
  
## <a name="see-also"></a>Vedere anche  
 [getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)   
 [Metodi di SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [Membri di SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Classe SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  
