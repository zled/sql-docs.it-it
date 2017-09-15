---
title: getUpdateCount (metodo) (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.getUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 50d702db72b2d02cc52401d76cd289a3b21de81a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getupdatecount-method-sqlserverstatement"></a>getUpdateCount (metodo) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il risultato corrente come conteggio aggiornamenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final int getUpdateCount()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che contiene il numero di aggiornamenti. Se il risultato restituito è un oggetto del set di risultati o se non è più disponibile alcun risultato, viene restituito -1.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getUpdateCount viene specificato dal metodo getUpdateCount nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
