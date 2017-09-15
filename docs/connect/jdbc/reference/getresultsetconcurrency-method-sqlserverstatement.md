---
title: Metodo (SQLServerStatement) getResultSetConcurrency | Documenti Microsoft
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
- SQLServerStatement.getResultSetConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 47ef6547-5ec7-4cf5-a4d4-e34cbeec72eb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 461001d8c584503b428414355eed14fc65e58791
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getresultsetconcurrency-method-sqlserverstatement"></a>getResultSetConcurrency (metodo) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il set di risultati per la concorrenza [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final int getResultSetConcurrency()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il tipo di concorrenza del set di risultati.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getResultSetConcurrency viene specificato dal metodo getResultSetConcurrency nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
