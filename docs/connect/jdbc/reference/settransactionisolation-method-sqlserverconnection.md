---
title: Metodo (SQLServerConnection) setTransactionIsolation | Documenti Microsoft
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
- SQLServerConnection.setTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6a8fa4d3-5237-40f8-8a02-b40a3d7a1131
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bd1a4fb0ef1c55c54a17dfe1825fd208ebd6035f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32846166"
---
# <a name="settransactionisolation-method-sqlserverconnection"></a>setTransactionIsolation (metodo) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tenta di modificare il livello di isolamento delle transazioni per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto a quello specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setTransactionIsolation(int level)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Livello*  
  
 Un **int** valore contenente uno dei livelli di isolamento seguenti:  
  
 TRANSACTION_READ_UNCOMMITTED  
  
 TRANSACTION_READ_COMMITTED  
  
 TRANSACTION_REPEATABLE_READ  
  
 TRANSACTION_SERIALIZABLE  
  
 TRANSACTION_SNAPSHOT = 0x1000  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setTransactionIsolation viene specificato dal metodo setTransactionIsolation nell'interfaccia Java.SQL. Connection.  
  
 Il commit delle transazioni non viene eseguito se questo metodo viene chiamato durante una transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
