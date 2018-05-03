---
title: Metodo updateClob (lang, Java.SQL. Clob) | Documenti Microsoft
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
- SQLServerResultSet.updateClob (java.lang.String, java.sql.Clob)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5da64915-1c13-44fd-90c0-52168889bae0
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa8e9e9886d728261f9dd9a3e54f3e3396a48754
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updateclob-method-javalangstring-javasqlclob"></a>Metodo updateClob (java.lang.String, java.sql.Clob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con il valore java.sql.Clob dopo che è stato specificato il nome della colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateClob(java.lang.String columnName,  
                       java.sql.Clob clobValue)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
 *clobValue*  
  
 Un oggetto Clob.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateClob viene specificato dal metodo updateClob nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateClob &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
