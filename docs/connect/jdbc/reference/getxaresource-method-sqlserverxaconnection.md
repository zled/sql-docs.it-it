---
title: Metodo getXAResource (SQLServerXAConnection) | Documenti Microsoft
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
- SQLServerXAConnection.getXAResource
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1d2828f-fd20-44b0-b796-dc70f77c5b03
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc93f1b4ee29d25893c64c7334c8ce6458354624
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getxaresource-method-sqlserverxaconnection"></a>Metodo getXAResource (SQLServerXAConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) che il gestore delle transazioni verrà utilizzato per gestire questo [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) la partecipazione dell'oggetto in una transazione distribuita.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public javax.transaction.xa.XAResource getXAResource()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto XAResource.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getXAResource viene specificato dal metodo getXAResource nell'interfaccia javax.SQL. XAConnection.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-methods.md)   
 [Membri di SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Classe SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
