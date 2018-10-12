---
title: Metodo getPooledConnection (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnectionPoolDataSource.getPooledConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f2e6391d-9aaf-4b09-ae1c-a27c1ada6301
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d6c21fa5df3545b641ccb935c53f6d7a689f580
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702949"
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
 *user*  
  
 Valore **String** contenente il nome utente.  
  
 *passwword*  
  
 Valore **String** che contiene la password.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md).  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getPooledConnection viene specificato dal metodo getPooledConnection nell'interfaccia ConnectionPoolDataSource.  
  
## <a name="see-also"></a>Vedere anche  
 [getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)   
 [Metodi di SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [Membri di SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Classe SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  
