---
title: Metodo setTransactionTimeout (SQLServerXAResource) | Documenti Microsoft
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
- SQLServerXAResource.setTransactionTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38bf4a1a-6ad3-437c-b9ed-8792ab6dde7e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4edf9eb64a8b6d42ae9d151e89eff0ce102af292
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="settransactiontimeout-method-sqlserverxaresource"></a>Metodo setTransactionTimeout (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il valore di timeout transazione corrente per questo [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean setTransactionTimeout(int seconds)  
```  
  
#### <a name="parameters"></a>Parametri  
 *secondi*  
  
 Un **int** valore.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il timeout è impostato correttamente. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setTransactionTimeout viene specificato dal metodo setTransactionTimeout nell'interfaccia javax.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Membri di SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Classe SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
