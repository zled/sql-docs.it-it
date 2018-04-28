---
title: Metodo addConnectionEventListener (SQLServerPooledConnection) | Documenti Microsoft
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
ms.topic: article
apiname:
- SQLServerPooledConnection.addConnectionEventListener
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 142830a8-8d4e-48ca-911d-85bf195ca4fe
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eebf0878a8a98fc19f10152944138be875327ca1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="addconnectioneventlistener-method-sqlserverpooledconnection"></a>Metodo addConnectionEventListener (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Registra il listener di eventi specificato in modo che verrà notificato quando si verifica un evento su questo [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void addConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Listener*  
  
 Un oggetto ConnectionEventListener.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo addConnectionEventListener viene specificato dal metodo addConnectionEventListener nell'interfaccia javax.SQL. PooledConnection.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [Membri di SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [Classe SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
