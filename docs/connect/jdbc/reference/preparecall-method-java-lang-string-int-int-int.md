---
title: Metodo prepareCall (lang, int, int, int) | Documenti Microsoft
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
- SQLServerConnection.prepareCall (java.lang.String, int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 81104fd5-75b0-4540-9f48-c3dbf59a8564
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ac3d0d3c239c76d187954e6a4568a140aba73ade
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="preparecall-method-javalangstring-int-int-int"></a>Metodo prepareCall (java.lang.String, int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) oggetto che genera l'errore [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetti con il tipo specificato, concorrenza e la trattenibilità.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql,  
                                              int nType,  
                                              int nConcur,  
                                              int nHold)  
```  
  
#### <a name="parameters"></a>Parametri  
 *SQL*  
  
 Oggetto **stringa** contenente un'istruzione SQL.  
  
 *NLE*  
  
 Un **int** che indica il set di risultati tipo.  
  
 *nConcur*  
  
 Un **int** che indica il tipo di concorrenza del set di risultati.  
  
 *nHold*  
  
 Un **int** che indica la trattenibilità dei set.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto CallableStatement.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo prepareCall viene specificato dal metodo prepareCall nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo prepareCall &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

