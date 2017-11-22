---
title: rowDeleted (metodo) (SQLServerResultSet) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.rowDeleted
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e4615318e2ca36d7524d25b0c5fcbf003711ee7
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="rowdeleted-method-sqlserverresultset"></a>rowDeleted (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera informazioni circa l'eventuale eliminazione di una riga.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se una riga viene eliminata e le eliminazioni vengono rilevate. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo rowDeleted viene specificato dal metodo rowDeleted nell'interfaccia Java.SQL. ResultSet.  
  
 Una riga eliminata potrebbe lasciare uno spazio vuoto visibile in un set di risultati. Questo metodo può essere utilizzato per rilevare gli spazi vuoti in un set di risultati. Il valore restituito dipende dal fatto che questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto è in grado di rilevare le eliminazioni.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]rileva le righe eliminate per tutti i tipi di cursore aggiornabili, anche se il rilevamento è temporaneo per i cursori forward e dinamici.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
