---
title: Metodo updateFloat (lang, float) | Documenti Microsoft
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
- SQLServerResultSet.updateFloat (java.lang.String, float)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 19a6164f-f560-4304-8466-e55f0667a3d4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b890cafc7582f50acc3c39fe3f31cb5211746796
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updatefloat-method-javalangstring-float"></a>Metodo updateFloat (java.lang.String, float)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un **float** valore in base al nome della colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateFloat(java.lang.String columnName,  
                        float x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
 *x*  
  
 Oggetto **float** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateFloat viene specificato dal metodo updateFloat nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateFloat &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
