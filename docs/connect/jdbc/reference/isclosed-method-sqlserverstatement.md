---
title: Metodo isClosed (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e79b5b53-16b0-42a3-be4e-542a77a21e12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bbd0e8ce34d14f0ef9fa77f3c2f64cc4e5804fb5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718329"
---
# <a name="isclosed-method-sqlserverstatement"></a>Metodo isClosed (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) è stato chiuso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se l'oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto è chiuso, **false** se è ancora aperto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo isClosed viene specificato dal metodo isClosed nell'interfaccia Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
