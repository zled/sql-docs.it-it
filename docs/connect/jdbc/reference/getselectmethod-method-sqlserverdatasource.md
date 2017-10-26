---
title: Metodo getSelectMethod (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.getSelectMethod
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6255d2e-0028-474a-afa8-553ef092243e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dae0422612846e25cb2d2a60273f753802df3da0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getselectmethod-method-sqlserverdatasource"></a>Metodo getSelectMethod (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il tipo di cursore predefinito utilizzato per tutti i set di risultati creati tramite questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getSelectMethod()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** valore contenente il tipo di cursore predefinito.  
  
## <a name="remarks"></a>Osservazioni  
 La proprietà selectMethod specifica il tipo di cursore predefinito che viene utilizzato per un set di risultati. Questa proprietà è utile in caso di set di risultati di grandi dimensioni e se non desidera archiviare tutto il set di risultati in memoria nel lato client. Impostando la proprietà su "cursor", è possibile creare un cursore sul lato server che può recuperare i blocchi di dati più piccoli in una sola volta. Se la proprietà selectMethod non è impostata, il metodo getSelectMethod restituisce il valore predefinito "direct".  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

