---
title: Metodo getBigDecimal (int, int) | Documenti Microsoft
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
- SQLServerCallableStatement.getBigDecimal (int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d9351b35-7046-4852-a612-72d4c46b2bbb
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1db4d021bd62ea484c4c6501c35a71b43c90377a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getbigdecimal-method-int-int"></a>Metodo getBigDecimal (int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro designato come oggetto java.math.BigDecimal in base all'indice del parametro e alla scala.  
  
> [!NOTE]  
>  Questo metodo è stato dichiarato deprecato dalla specifica JDBC. Utilizzare invece il [getBigDecimal (int)](../../../connect/jdbc/reference/getbigdecimal-method-int.md) metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.math.BigDecimal getBigDecimal(int index,  
                                          int scale)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Un **int** che indica l'indice del parametro.  
  
 *scala*  
  
 Un **int** che indica il numero di cifre a destra del separatore decimale.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto BigDecimal.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getBigDecimal viene specificato dal metodo getBigDecimal nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getBigDecimal &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
