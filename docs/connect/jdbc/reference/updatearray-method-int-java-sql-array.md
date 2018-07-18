---
title: Metodo updateArray (int, Java.SQL. Array) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateArray (int, java.sql.Array)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 464f7e3f-3e8a-4b2d-aebd-1c040583d52c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 80491fd2fe637dae26860e2b6b02dd06fe5fc04e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32849206"
---
# <a name="updatearray-method-int-javasqlarray"></a>Metodo updateArray (int, java.sql.Array)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un oggetto matrice base all'indice di colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateArray(int columnIndex,  
                        java.sql.Array x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
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
  
  
