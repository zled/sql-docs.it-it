---
title: Metodo Prepare (SQLServerXAResource) | Documenti Microsoft
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
- SQLServerXAResource.prepare
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f800c966-3fae-41b3-963a-464988f80da3
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aba0a7000dccfe881ccd8c755f548013f3798559
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="prepare-method-sqlserverxaresource"></a>Metodo prepare (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Richieste di Prepara il gestore delle risorse per un commit della transazione specificata dall'oggetto Xid specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int prepare(javax.transaction.xa.Xid xid)  
```  
  
#### <a name="parameters"></a>Parametri  
 *XID*  
  
 Oggetto Xid.  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo di preparazione è specificato dal metodo nell'interfaccia javax prepare.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Membri di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Classe SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
