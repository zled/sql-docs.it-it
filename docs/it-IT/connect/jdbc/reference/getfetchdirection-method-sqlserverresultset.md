---
title: getFetchDirection (metodo) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ab385c2-e18c-4b75-ac2d-2402af5c52a5
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 953b198a51d0b9def12e8d9df81920f424641fca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getfetchdirection-method-sqlserverresultset"></a>getFetchDirection (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la direzione di recupero per questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getFetchDirection()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica la direzione di recupero corrente.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getFetchDirection viene specificato dal metodo getFetchDirection nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo restituisce FETCH_FORWARD per i cursori forward-only, l'ultima impostazione eseguita da una chiamata per il [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md) metodo per altri tipi di cursore e restituirà FETCH_UNKNOWN per questi tipi di cursore se il metodo setFetchDirection non è stato chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
