---
title: Metodo updateBigDecimal (int, BigDecimal) | Documenti Microsoft
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
- SQLServerResultSet.updateBigDecimal (int, java.math.BigDecimal)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1e15de27-a490-45cd-a3a6-a49721f15a97
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ccb1fa9ab184f7357323c5d8deb417b93ec7985e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32849116"
---
# <a name="updatebigdecimal-method-int-javamathbigdecimal"></a>Metodo updateBigDecimal (int, java.math.BigDecimal)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un oggetto di BigDecimal in base all'indice di colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateBigDecimal(int index,  
                             java.math.BigDecimal x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Un **int** che indica l'indice di colonna.  
  
 *x*  
  
 Un oggetto BigDecimal.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updateBigDecimal viene specificato dal metodo updateBigDecimal nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateBigDecimal &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatebigdecimal-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
