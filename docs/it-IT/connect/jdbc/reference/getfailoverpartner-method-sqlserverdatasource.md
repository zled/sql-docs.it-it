---
title: Metodo getFailoverPartner (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.getFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 885f927f-9c48-42e0-a7fb-fd936d2b8130
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6330d85cd9625854049ef5ec51bedff223a23198
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getfailoverpartner-method-sqlserverdatasource"></a>Metodo getFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il nome del server di failover utilizzato nella configurazione del mirroring del database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public string getFailoverPartner()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il nome del partner di failover, oppure null se non è impostato.  
  
## <a name="remarks"></a>Osservazioni  
 Il valore restituito da questo metodo riflette il failover partner nome set mediante il [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
