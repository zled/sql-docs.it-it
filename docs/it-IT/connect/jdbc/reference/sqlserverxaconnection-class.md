---
title: Classe SQLServerXAConnection | Documenti Microsoft
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
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba48701c441a75f0d7c6b7f78c964384c47f94e7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverxaconnection-class"></a>Classe SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta le connessioni JDBC che possono partecipare alle transazioni distribuite (XA).  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **Implementa:** XAConnection  
  
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
  
  
