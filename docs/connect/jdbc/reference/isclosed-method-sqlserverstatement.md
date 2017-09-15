---
title: Metodo isClosed (SQLServerStatement) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e79b5b53-16b0-42a3-be4e-542a77a21e12
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fdd47545dcf4962eca79dc764b03f63f72d20343
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="isclosed-method-sqlserverstatement"></a>Metodo isClosed (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto è stato chiuso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto è chiuso, **false** se è ancora aperto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo isClosed viene specificato dal metodo isClosed nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
