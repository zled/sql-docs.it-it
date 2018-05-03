---
title: Metodo updateLong (int, long) | Documenti Microsoft
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
- SQLServerResultSet.updateLong (int, long)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6363288-1415-4b25-8bb3-c34d6211c6d7
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c1454e1ffdee7e5ac5db7261606b298d4946e9e1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updatelong-method-int-long"></a>Metodo updateLong (int, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un **lungo** valore in base all'indice di colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateLong(int index,  
                       long x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Un **int** che indica l'indice di colonna.  
  
 *x*  
  
 Oggetto **lungo** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateLong viene specificato dal metodo updateLong nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateLong &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatelong-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
