---
title: Metodo (SQLServerConnection) getStatementHandleCacheEntryCount | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
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
- SQLServerConnection.getStatementHandleCacheEntryCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0f29ad007c4f3b60694963c9f3f7b71763c7b9fa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getstatementhandlecacheentrycount-method-sqlserverconnection"></a>getStatementHandleCacheEntryCount metodo (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Restituisce il numero corrente di handle di istruzione preparata in pool.

## <a name="syntax"></a>Sintassi  
  
```  
  
public int getStatementHandleCacheEntryCount()  
```  

## <a name="return-value"></a>Valore restituito
 Un **int** che contiene il numero corrente di handle di istruzione preparata in pool.

## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Osservazioni  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e successivo.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
