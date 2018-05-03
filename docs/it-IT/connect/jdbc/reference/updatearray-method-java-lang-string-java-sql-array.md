---
title: Metodo updateArray (lang, Java.SQL. Array) | Documenti Microsoft
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
- SQLServerResultSet.updateArray (java.lang.String, java.sql.Array)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6f2ced5a-1c7d-439a-aaa5-472b9f4fdeab
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60945f2dbb278c5c7bb98e54b14b6a584fa8c00a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updatearray-method-javalangstring-javasqlarray"></a>Metodo updateArray (java.lang.String, java.sql.Array)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un oggetto matrice dato il nome della colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateArray(java.lang.String columnName,  
                        java.sql.Array x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
 *x*  
  
 Oggetto matrice.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateArray viene specificato dal metodo updateArray nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateArray &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatearray-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
