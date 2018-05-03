---
title: Metodo (SQLServerConnection) getTransactionIsolation | Documenti Microsoft
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
- SQLServerConnection.getTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 179772e9-6572-4ce5-83c5-ab2b196cee67
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58c373095c63f3cd13294b7c472bea741e71b55c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="gettransactionisolation-method-sqlserverconnection"></a>getTransactionIsolation (metodo) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il livello di isolamento transazione corrente di questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getTransactionIsolation()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** valore contenente uno dei livelli di isolamento seguenti:  
  
 TRANSACTION_NONE  
  
 TRANSACTION_READ_UNCOMMITTED  
  
 TRANSACTION_READ_COMMITTED  
  
 TRANSACTION_REPEATABLE_READ  
  
 TRANSACTION_SERIALIZABLE  
  
 TRANSACTION_SNAPSHOT = 0x1000  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getTransactionIsolation viene specificato dal metodo getTransactionIsolation nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
