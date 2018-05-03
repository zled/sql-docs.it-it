---
title: Metodo (SQLServerConnection) getAutoCommit | Documenti Microsoft
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
- SQLServerConnection.getAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: af1f67f4-f568-4e58-abcc-5c809a89b547
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 639a53f4c8eaabb0766e47c82cbcbb3e6c94e201
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getautocommit-method-sqlserverconnection"></a>getAutoCommit (metodo) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la modalità autocommit corrente per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean getAutoCommit()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la modalità autocommit è abilitata, **false** in caso contrario.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getAutoCommit viene specificato dal metodo getAutoCommit nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
