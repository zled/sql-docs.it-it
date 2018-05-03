---
title: Rollback (Java.SQL. savePoint) metodo | Documenti Microsoft
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
- SQLServerConnection.rollback (java.sql.Savepoint)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d5dbd9ef-194f-4130-bfcc-7901a4fa8ded
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd3f71c5ecef7962e7dde08efd1c744539883228
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="rollback-method-javasqlsavepoint"></a>Metodo rollback (java.sql.Savepoint)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Annulla tutte le modifiche apportate dopo il determinato [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) oggetto è stato impostato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void rollback(java.sql.Savepoint s)  
```  
  
#### <a name="parameters"></a>Parametri  
 *S*  
  
 L'oggetto punto di salvataggio di eseguire il rollback.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo di rollBack viene specificato dal metodo rollBack nell'interfaccia Java.SQL. Connection.  
  
 Questo metodo deve essere utilizzato solo quando la modalità autocommit è stata disabilitata.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Rollback &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
