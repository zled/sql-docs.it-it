---
title: Metodo (SQLServerStatement) getMaxRows | Documenti Microsoft
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
- SQLServerStatement.getMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6aece4e5-027d-434e-a8cf-a67c0484f189
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d9f64d60a08727f239ca3eee4354fc094e06107a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getmaxrows-method-sqlserverstatement"></a>getMaxRows (metodo) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il numero massimo di righe che un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto generato da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto può contenere.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final int getMaxRows()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il numero massimo di righe oppure 0 se non esiste alcun limite.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getMaxRows viene specificato dal metodo getMaxRows nell'interfaccia Java.SQL. Statement.  
  
 Questo metodo getMaxRows restituisce sempre 0 per i cursori scorrevoli dinamici.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

