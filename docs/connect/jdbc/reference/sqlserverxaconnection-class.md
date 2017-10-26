---
title: Classe SQLServerXAConnection | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f885d32d2887a9db7c7159025713616c560437c9
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxaconnection-class"></a>Classe SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta le connessioni JDBC che possono partecipare alle transazioni distribuite (XA).  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Implementa:** javax.SQL. XAConnection  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>Osservazioni  
 È possibile integrare un oggetto SQLServerXAConnection in una transazione distribuita per mezzo di un [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) oggetto. Un gestore delle transazioni, generalmente parte di un server di livello intermedio, gestisce un oggetto SQLServerXAConnection tramite l'oggetto SQLServerXAResource.  
  
> [!NOTE]  
>  I programmatori di applicazioni in genere non utilizzano direttamente questa interfaccia. Viene utilizzata principalmente da un responsabile transazioni che utilizza il server di livello intermedio.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

