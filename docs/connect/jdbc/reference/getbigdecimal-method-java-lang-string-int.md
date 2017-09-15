---
title: Metodo getBigDecimal (lang, int) | Documenti Microsoft
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
- SQLServerCallableStatement.getBigDecimal (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6967ba55-9c9a-4f6f-a4d2-8ee9c9a82c14
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1f47ef135f367e5263616aec8a29cd3693967974
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getbigdecimal-method-javalangstring-int"></a>Metodo getBigDecimal (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro designato come oggetto java.math.BigDecimal in base al nome del parametro e alla scala.  
  
> [!NOTE]  
>  Questo metodo è stato dichiarato deprecato dalla specifica JDBC. Utilizzare invece il [getBigDecimal (lang)](../../../connect/jdbc/reference/getbigdecimal-method-java-lang-string.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String sCol,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCol*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
 *scala*  
  
 Un **int** che indica il numero di cifre a destra del separatore decimale.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto BigDecimal.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getBigDecimal viene specificato dal metodo getBigDecimal nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getBigDecimal &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
