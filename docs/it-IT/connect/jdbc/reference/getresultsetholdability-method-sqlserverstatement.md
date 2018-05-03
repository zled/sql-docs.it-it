---
title: Metodo (SQLServerStatement) getResultSetHoldability | Documenti Microsoft
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
- SQLServerStatement.getResultSetHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 053549ee-2018-47ab-9538-789dac2b150a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d197775f572eded579e85050cb82840e6c50c67a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getresultsetholdability-method-sqlserverstatement"></a>getResultSetHoldability (metodo) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il set di risultati trattenibilità per [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti generati da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final int getResultSetHoldability()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica la trattenibilità dei set.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getResultSetHoldability viene specificato dal metodo getResultSetHoldability nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
