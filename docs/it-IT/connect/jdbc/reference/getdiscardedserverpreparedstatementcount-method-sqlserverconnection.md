---
title: Metodo (SQLServerConnection) getDiscardedServerPreparedStatementCount | Documenti Microsoft
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
- SQLServerConnection.getDiscardedServerPreparedStatementCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5087356ceefe7b9b9dd154b9286f5be5c18dc4c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getdiscardedserverpreparedstatementcount-method-sqlserverconnection"></a>getDiscardedServerPreparedStatementCount metodo (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Restituisce il numero di attualmente in attesa preparata istruzione unprepare azioni.

## <a name="syntax"></a>Sintassi  
  
```  
  
public int getDiscardedServerPreparedStatementCount()  
```  

## <a name="return-value"></a>Valore restituito
 Un **int** che contiene il numero di istruzione preparata in attesa non preparato azioni.

## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Osservazioni  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e successivo.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
