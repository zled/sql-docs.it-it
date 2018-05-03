---
title: Metodo updateRef (int, Java.SQL. ref) | Documenti Microsoft
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
- SQLServerResultSet.updateRef (int, java.sql.Ref)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eab3ebae-3f68-4303-869a-fee06e3a9c71
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d9432aa7cedb3ca130128f37afdb95d42301332
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updateref-method-int-javasqlref"></a>Metodo updateRef (int, java.sql.Ref)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore java.sql.Ref in base all'indice di colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateRef(int columnIndex,  
                      java.sql.Ref x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
 *x*  
  
 Un oggetto di riferimento.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateRef viene specificato dal metodo updateRef nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateRef &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateref-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
