---
title: Metodo Rollback (SQLServerXAResource) | Documenti Microsoft
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
- SQLServerXAResource.rollback
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 93d9d7e6-54b6-4d86-8f8c-386c6057e85e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2ce0570cf86b864bc76e012ca2288e1a2f595334
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="rollback-method-sqlserverxaresource"></a>Metodo rollback (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Richiede che il lavoro di rollback dello strumento di gestione delle risorse venga eseguito per conto di un ramo di transazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void rollback(javax.transaction.xa.Xid xid)  
```  
  
#### <a name="parameters"></a>Parametri  
 *XID*  
  
 Oggetto Xid.  
  
## <a name="exceptions"></a>Eccezioni  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo di rollback viene specificato dal metodo nell'interfaccia javax rollback.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Membri di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Classe SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
