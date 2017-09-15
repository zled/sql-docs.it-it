---
title: Metodo getBigDecimal (int, int) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.getBigDecimal (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c99d0772-b26c-492c-a643-2813b5429993
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2a85dff4212c53a76fb26a0c9296ced2197388d8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getbigdecimal-method-int-int-sqlserverresultset"></a>Metodo getBigDecimal (int, int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore di indice della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto tramite la scala specificata.  
  
> [!NOTE]  
>  Questo metodo è stato dichiarato deprecato dalla specifica JDBC. Utilizzare invece il [getBigDecimal (int)](../../../connect/jdbc/reference/getbigdecimal-method-int-sqlserverresultset.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.math.BigDecimal getBigDecimal(int columnIndex,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
 *scala*  
  
 Un **int** che indica il numero di cifre a destra del separatore decimale.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto BigDecimal.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getBigDecimal viene specificato dal metodo getBigDecimal nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getBigDecimal &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
