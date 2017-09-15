---
title: Metodo getQueryTimeout (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.getQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8dff954f-b458-4fa6-abe6-be62ff75e2b9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fff7b7d5310caf4ea57d929037c82aff1ae3f024
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getquerytimeout-method-sqlserverstatement"></a>Metodo getQueryTimeout (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il numero di secondi [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] dovrà attendere [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto per l'esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final int getQueryTimeout()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il numero di secondi di attesa del driver JDBC oppure 0 se non esiste alcun limite.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getQueryTimeout viene specificato dal metodo getQueryTimeout nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
