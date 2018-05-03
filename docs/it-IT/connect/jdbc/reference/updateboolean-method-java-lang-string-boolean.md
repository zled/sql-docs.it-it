---
title: Metodo (lang, booleano) updateBoolean | Documenti Microsoft
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
- SQLServerResultSet.updateBoolean (java.lang.String, boolean)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5fed9ebb-d9a3-4d1a-9212-1057a603c4e5
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3df504387253c81eef3b041348138f5276df89af
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updateboolean-method-javalangstring-boolean"></a>Metodo updateBoolean (java.lang.String, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un **booleano** valore in base al nome della colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateBoolean(java.lang.String columnName,  
                          boolean x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
 *x*  
  
 Oggetto **booleano** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateBoolean viene specificato dal metodo updateBoolean nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateBoolean &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateboolean-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
