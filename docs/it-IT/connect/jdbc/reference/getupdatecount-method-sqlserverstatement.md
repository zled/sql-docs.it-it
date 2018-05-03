---
title: getUpdateCount (metodo) (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.getUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ec60f62adb3be2752bf460d88460f5ce91b18ee
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
  
