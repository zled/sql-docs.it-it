---
title: Metodo getClientConnectionID (SQLServerConnection) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bee39c11-733a-461f-92cc-33efcb2af87d
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: be59e3cb669c9ac62b11901cc548a8223dd9e2f4
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="getclientconnectionid-method-sqlserverconnection"></a>Metodo getClientConnectionID (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ottiene l'ID connessione del tentativo di connessione più recente, indipendentemente dalla riuscita o meno del tentativo.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
public Java.util.UUID SQLServerConnection.getClientConnectionID();  
```  
  
## <a name="return-value"></a>Valore restituito  
 GUID a 16 byte che rappresenta l'ID connessione del tentativo di connessione più recente oppure NULL in caso di errore dopo aver avviato la richiesta di connessione e l'handshake pre-login.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sull'accesso alle informazioni di diagnostica nel log degli eventi estesi, vedere [l'accesso a informazioni di diagnostica nel Log degli eventi estesi](../../../connect/jdbc/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
 Nell'esempio seguente viene mostrato come ottenere l'ID connessione:  
  
```  
Connection con = DriverManager.getConnection(connectionUrl);  
UUID id = ((ISQLServerConnection)con).getClientConnectionId();  
```  
  
 Nell'esempio seguente viene mostrato come ottenere l'ID connessione in modo diverso:  
  
```  
SQLServerConnectionPoolDataSource ds = new SQLServerConnectionPoolDataSource();  
ds.setUser("…");  
ds.setPassword("…");  
ds.setServerName("…");  
PooledConnection pcon= ds.getPooledConnection();  
Connection cn = pcon.getConnection();  
UUID conid = ((ISQLServerConnection)cn).getClientConnectionId();  
```  
  
 **getClientConnectionID** funziona indipendentemente dalla versione del server si connette a, ma i registri eventi estesi e voce degli errori del buffer circolare di connettività non saranno presenti in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 2008 R2 e versioni precedenti.  
  
 È possibile individuare l'ID connessione nel log degli eventi estesi per verificare se l'errore sia nel server qualora l'evento esteso per la registrazione dell'ID connessione sia abilitato. È anche possibile individuare l'ID di connessione nel buffer circolare di connessione ([la risoluzione dei problemi di connettività in SQL Server 2008 con il Buffer circolare di connettività](http://go.microsoft.com/fwlink/?LinkId=207752)) per determinati errori di connessione. Se l'ID connessione non si trova nel buffer circolare di connessione, si può presumere che si tratti di un errore di rete.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
