---
title: Metodo Absolute (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.absolute
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 638e8148-8ca0-4e1f-9ec2-04a11bc9809b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30594c58b1ccd24c68f9e4f4468fc7f31378d074
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="absolute-method-sqlserverresultset"></a>Metodo Absolute (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sposta il cursore nella riga specificata in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean absolute(int row)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Riga*  
  
 Un **int** che indica il numero di riga in cui spostarsi. Può essere positivo, negativo o 0.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il cursore viene spostato nella posizione specificata. **false** se prima della prima riga o dopo l'ultima riga.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo assoluto viene specificato dal metodo nell'interfaccia Java.SQL. ResultSet assoluto.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
