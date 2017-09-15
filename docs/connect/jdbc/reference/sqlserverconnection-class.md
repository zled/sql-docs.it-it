---
title: Classe SQLServerConnection | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 937292a6-1525-423e-a2b2-a18fd34c2893
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a3beda0e5629888804b522e5c4e3123e0b959ba8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverconnection-class"></a>Classe SQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta una connessione JDBC a un [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Implementa:** [ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md), Java.IO. Serializable  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerConnection  
```  
  
## <a name="remarks"></a>Osservazioni  
 SQLServerConnection supporta il pool di connessioni JDBC e può essere una connessione JDBC fisica o logica. SQLServerConnection gestisce il controllo delle transazioni per tutte le istruzioni create e può partecipare alle transazioni distribuite XA gestite tramite un adattatore XAResource.  
  
 SQLServerConnection gestisce un pool di handle di istruzione preparata. Tali istruzioni vengono preparate una volta e vengono generalmente eseguite più volte con valori dei dati diversi per i relativi parametri. Le istruzioni preparate vengono gestite anche nelle operazioni di chiusura della connessione logica (in pool).  
  
> [!NOTE]  
>  SQLServerConnection non è thread-safe. Tuttavia, è possibile elaborare contemporaneamente in thread simultanei più istruzioni create da una singola connessione.  
  
 Questa classe supporta l'annullamento del wrapping nella classe SQLServerConnection, interfaccia Java.SQL. Connection e interfaccia ISQLServerConnection. Per ulteriori informazioni, vedere [wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
