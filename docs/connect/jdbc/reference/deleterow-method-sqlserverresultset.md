---
title: deleteRow (metodo) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd06dec2dccd3e124d702131aa4520a394ecd9fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830106"
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
  
  
