---
title: Utilizzando pool di connessioni | Documenti Microsoft
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
ms.assetid: 699d4e8a-34bf-4c60-b0d5-4a10dad6084a
caps.latest.revision: "30"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b0125330ff44030e354423b105710fc6806f337
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="using-connection-pooling"></a>Utilizzo del pool di connessioni
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il supporto per Java Platform, Enterprise Edition (Java EE) il pool di connessioni. Il driver JDBC implementa le interfacce richieste della versione JDBC 3.0 per consentire al driver di partecipare all'implementazione del pool di connessioni del fornitore di applicazioni middleware conformi con JDBC 3.0. Applicazioni middleware quali i server di applicazioni Java EE offrono spesso servizi aggiuntivi conformi con il pool di connessioni. Il driver JDBC parteciperà alle connessioni in pool in questi ambienti.  
  
> [!NOTE]  
>  Sebbene il driver JDBC supporti il pool di connessioni Java EE, non è tuttavia in grado di fornire la propria implementazione del pool. Per la gestione delle connessioni, il driver si basa su server applicazioni Java di terze parti.  
  
## <a name="remarks"></a>Osservazioni  
 Le classi per l'implementazione del pool di connessioni sono le seguenti:  
  
|Classe|Implementa|Description|  
|-----------|----------------|-----------------|  
|com.microsoft.SqlServer.JDBC. SQLServerXADataSource|javax.sql.ConnectionPoolDataSource e javax.sql.XADataSource|È consigliabile utilizzare il [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) necessita di classe per tutti i server Java EE, in quanto implementa tutte le interfacce di pool JDBC 3.0 e XA.|  
|com.microsoft.SqlServer.JDBC. SQLServerConnectionPoolDataSource|javax.sql.ConnectionPoolDataSource|Questa classe è una connection factory che consente al server applicazioni Java EE di inserire il proprio pool di connessioni nelle connessioni fisiche. Se la configurazione del fornitore Java EE richiede una classe che implementa javax.SQL. ConnectionPoolDataSource, specificare il nome della classe come [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md). In genere, si consiglia di utilizzare il [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) classe, in quanto implementa entrambe pool e XA interfacce ed è stata verificata in più configurazioni del server Java EE.|  
  
 Il codice dell'applicazione JDBC deve sempre chiudere esplicitamente le connessioni per trarre il massimo vantaggio dal pool. Quando l'applicazione chiude in modo esplicito una connessione, l'implementazione del pool consente di riutilizzare immediatamente la connessione. Se la connessione non viene chiusa, le altre applicazioni non possono riutilizzarla. Le applicazioni possono utilizzare il `finally` costrutto per assicurarsi che le connessioni in pool siano chiuse anche se si verifica un'eccezione.  
  
> [!NOTE]  
>  Il driver JDBC non chiama attualmente la stored procedure sp_reset_connection quando restituisce la connessione al pool, ma si basa su server applicazioni Java di terze parti per restituire le connessioni allo stato originale.  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione a SQL Server con il driver JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
