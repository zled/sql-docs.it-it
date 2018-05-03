---
title: Metodo (lang) executeQuery | Documenti Microsoft
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
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32d5df3beda3155bd11c6077982ceec5e7daace5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="executequery-method-javalangstring"></a>Metodo executeQuery (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esegue l'istruzione SQL specificata e restituisce un singolo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Oggetto **stringa** che contiene un'istruzione SQL.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto SQLServerResultSet.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo executeQuery viene specificato dal metodo executeQuery nell'interfaccia Java.SQL. Statement.  
  
 Questo metodo esegue l'override di [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) metodo presente nel [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) classe.  
  
 Chiamare questo metodo comporterà un'eccezione poiché l'istruzione SQL per l'oggetto SQLServerPreparedStatement non viene specificato quando viene creato l'oggetto.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) viene generata se l'istruzione SQL specificata produce qualsiasi oggetto tranne un singolo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo executeQuery &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
