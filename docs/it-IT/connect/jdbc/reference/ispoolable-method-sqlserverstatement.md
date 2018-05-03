---
title: Metodo (SQLServerStatement) isPoolable | Documenti Microsoft
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
ms.assetid: b8a12ac5-57cb-4288-9973-c7d5cebd197c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0573dfa6f3497ee1275d986d3b24bd88b083aae1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ispoolable-method-sqlserverstatement"></a>isPoolable (metodo) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un valore che indica se è possibile aggiungere un'istruzione al pool di istruzioni fornito dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isPoolable() throws SQLException  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se l'istruzione può essere aggiunto al pool di istruzioni fornito dall'utente; **false** in caso contrario.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 [setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md) modifica il comportamento di un oggetto in pool.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
