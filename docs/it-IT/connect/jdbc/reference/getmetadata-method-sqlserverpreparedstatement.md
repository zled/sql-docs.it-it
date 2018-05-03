---
title: getMetaData (metodo) (SQLServerPreparedStatement) | Documenti Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.getMetaData
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ed49a53-ed61-4e95-ad67-45957aaabb6a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e593e5bf87a75c5b2feead3d117f1a7811337189
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
  
