---
title: Metodo (SQLServerResultSet) isAfterLast | Documenti Microsoft
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
- SQLServerResultSet.isAfterLast
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 19f9d124-3184-4985-8b97-503a8ab8b4f9
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fbcda8bde682b8f86028faa3dcd0df1475a0618f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843066"
---
# <a name="isafterlast-method-sqlserverresultset"></a>isAfterLast (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Specifica se il cursore si trova dopo l'ultima riga in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isAfterLast()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il cursore si trova dopo l'ultima riga. **false** se il cursore si trova in qualsiasi altra posizione o se il set di risultati non contiene righe.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo isAfterLast viene specificato dal metodo isAfterLast nell'interfaccia Java.SQL. ResultSet.  
  
 Se questo metodo viene utilizzato con cursori dinamici, inclusi i cursori di sola lettura forward-only, e la proprietà di connessione selectMethod viene impostata su "cursor", si verificherà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
