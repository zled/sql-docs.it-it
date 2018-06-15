---
title: Metodo addConnectionEventListener (SQLServerPooledConnection) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
ms.openlocfilehash: 6482521780045b1d5f0482731c1b6f8e2f5f3571
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32828266"
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
  
  
