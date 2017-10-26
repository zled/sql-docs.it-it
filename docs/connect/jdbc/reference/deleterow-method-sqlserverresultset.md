---
title: deleteRow (metodo) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3759d1d938d45bd952fa589ba47ac7c2d97dcefe
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="deleterow-method-sqlserverresultset"></a>deleteRow (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Elimina la riga corrente da questo[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto e dal database sottostante.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void deleteRow()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo deleteRow viene specificato dal metodo deleteRow nell'interfaccia Java.SQL. ResultSet.  
  
 Non è possibile chiamare questo metodo quando il cursore si trova sulla riga di inserimento.  
  
 In caso di utilizzo di cursori keyset, questo metodo lascia uno spazio vuoto nel set di risultati. È possibile verificare questo spazio vuoto utilizzando il [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md) metodo. I numeri delle righe del set di risultati non cambiano.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

