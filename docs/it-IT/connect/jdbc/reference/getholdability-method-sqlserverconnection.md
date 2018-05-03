---
title: Metodo (SQLServerConnection) getHoldability | Documenti Microsoft
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
apiname:
- SQLServerConnection.getHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b1644791-c36a-4837-86c4-9299537ee1c2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d3cc5eda382ba6de85b1610d11fa3d2cadeb203
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getholdability-method-sqlserverconnection"></a>getHoldability, metodo (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la trattenibilità corrente [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti creati tramite questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** valore contenente uno dei livelli di trattenibilità seguenti:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getHoldability viene specificato dal metodo getHoldability nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
