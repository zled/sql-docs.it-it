---
title: Metodo Absolute (SQLServerResultSet) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.absolute
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 638e8148-8ca0-4e1f-9ec2-04a11bc9809b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c952c24cfab1a36715d98cf0aad6caad7212a601
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="absolute-method-sqlserverresultset"></a>Metodo Absolute (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sposta il cursore nella riga specificata in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean absolute(int row)  
```  
  
#### <a name="parameters"></a>Parametri  
 *riga*  
  
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
  
  
