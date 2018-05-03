---
title: Metodo wasNull (SQLServerCallableStatement) | Documenti Microsoft
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
- SQLServerCallableStatement.wasNull
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1a27b2fe-ae12-46a9-9bca-2c5ca66b9eb3
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95519d428b37b04b9260a96b60c104086e2d1d4f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="wasnull-method-sqlservercallablestatement"></a>Metodo wasNull (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera informazioni circa l'eventuale impostazione del valore SQL NULL per l'ultimo parametro OUT letto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean wasNull()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se l'ultimo parametro letto era null. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo wasNull viene specificato dal metodo wasNull nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
