---
title: Metodo updateInt (lang, int) | Documenti Microsoft
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
- SQLServerResultSet.updateInt (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b0aef8f7-057e-4b57-892c-d120f2daed77
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5d4849c3f47fc7289cf84fe12f8703dd2adc4c1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updateint-method-javalangstring-int"></a>Metodo updateInt (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un **int** valore in base al nome della colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateInt(java.lang.String columnName,  
                      int x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
 *x*  
  
 Un **int** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateInt viene specificato dal metodo updateInt nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateInt &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
