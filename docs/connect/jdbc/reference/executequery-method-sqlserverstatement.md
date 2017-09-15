---
title: Metodo executeQuery (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.executeQuery
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 599cf463-e19f-4baa-bacb-513cad7c6cd8
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 806cde82a3e1556ef4df93eb4916ae14ae19c8c9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="executequery-method-sqlserverstatement"></a>Metodo executeQuery (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esegue l'istruzione SQL specificata e restituisce un singolo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *SQL*  
  
 Oggetto **stringa** che contiene un'istruzione SQL.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto SQLServerResultSet.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo executeQuery viene specificato dal metodo executeQuery nell'interfaccia Java.SQL. Statement.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) viene generata se l'istruzione SQL specificata produce qualsiasi oggetto tranne un singolo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
 Se l'esecuzione di una stored procedure restituisce un conteggio di aggiornamento che è maggiore di uno o genera più set di risultati, utilizzare il [eseguire](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) metodo per eseguire la stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
