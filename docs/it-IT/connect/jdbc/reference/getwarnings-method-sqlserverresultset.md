---
title: Metodo getWarnings (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.getWarnings
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb4339b0-383b-4337-a935-e8ec3f0d4123
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8979706ccaca1284bb8454ce51937ab227dbcb11
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getwarnings-method-sqlserverresultset"></a>Metodo getWarnings (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il primo avviso segnalato dalle chiamate a questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
> [!NOTE]  
>  Questo metodo non è attualmente supportato per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Se viene chiamato, restituirà sempre un valore Null.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.SQLWarning getWarnings()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto SQLWarning.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getWarnings viene specificato dal metodo getWarnings nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
