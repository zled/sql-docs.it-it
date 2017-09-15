---
title: getMetaData (metodo) (SQLServerPreparedStatement) | Documenti Microsoft
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
- SQLServerPreparedStatement.getMetaData
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ed49a53-ed61-4e95-ad67-45957aaabb6a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fa53555385ae6b23bef278ff4456ee8d5ab7f50f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getmetadata-method-sqlserverpreparedstatement"></a>getMetaData (metodo) (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un [classe SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) oggetto che contiene informazioni sulle colonne di [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetti che verranno restituiti quando questo [ SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) viene eseguito l'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final java.sql.ResultSetMetaData getMetaData()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto ResultSetMetaData.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getMetaData viene specificato dal metodo getMetaData nell'interfaccia Java.SQL. PreparedStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
