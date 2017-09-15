---
title: Metodo supportsExpressionsInOrderBy (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.supportsExpressionsInOrderBy
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 858f3c02-4531-4775-97e9-a03b316bdaba
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc260d583a7ee26647d00863b9027b73efba5a69
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="supportsexpressionsinorderby-method-sqlserverdatabasemetadata"></a>Metodo supportsExpressionsInOrderBy (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database supporta espressioni negli elenchi ORDER BY.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsExpressionsInOrderBy()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo supportsExpressionsInOrderBy viene specificato dal metodo supportsExpressionsInOrderBy nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
