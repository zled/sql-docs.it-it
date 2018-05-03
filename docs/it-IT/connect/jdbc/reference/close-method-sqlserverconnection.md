---
title: Close (metodo) (SQLServerConnection) | Documenti Microsoft
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
- SQLServerConnection.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f0f26585-bdf7-4737-b434-8c7e115c8e94
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5cd2dfa16c670b89f22982e41cc6fa50d7f9b187
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="close-method-sqlserverconnection"></a>Close (metodo) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rilascia questa [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) database e le risorse JDBC immediatamente anziché attendere che vengano automaticamente rilasciate dell'oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo close è specificato dal metodo di chiusura nell'interfaccia Java.SQL. Connection.  
  
 Chiamare il metodo close durante una transazione comporta il rollback della transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
