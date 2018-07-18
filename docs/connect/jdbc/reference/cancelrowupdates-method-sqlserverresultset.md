---
title: cancelRowUpdates (metodo) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.cancelRowUpdates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ecacca4-f7bc-4f5d-886a-da7747fdccae
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0ede77955a4a31cf548109045ca75879f15232d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32828536"
---
# <a name="cancelrowupdates-method-sqlserverresultset"></a>cancelRowUpdates (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Annulla gli aggiornamenti apportati alla riga corrente in questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void cancelRowUpdates()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo cancelRowUpdates viene specificato dal metodo cancelRowUpdates nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo può essere chiamato dopo la chiamata al metodo di aggiornamento e prima di chiamare il [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) metodo rollback degli aggiornamenti che sono stati apportati a una riga. Se non sono stati effettuati aggiornamenti o è già stato chiamato updateRow, questo metodo non ha alcun effetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
