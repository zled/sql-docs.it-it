---
title: Informazioni sulle transazioni | Documenti Microsoft
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
ms.topic: article
ms.assetid: d3e0414c-6809-4bb1-93b1-4960507faecc
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7a0d737f8cbbcb09d67a73589c5e2a0a37c64d54
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="understanding-transactions"></a>Informazioni sulle transazioni
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le transazioni sono gruppi di operazioni combinate in unità di lavoro logiche. Vengono utilizzate per controllare e mantenere la consistenza e l'integrità di ogni azione di una transazione, nonostante gli errori che possono verificarsi nel sistema.  
  
 Con il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], le transazioni possono essere locali o distribuite. Nelle transazioni possono inoltre essere utilizzati livelli di isolamento. Per ulteriori informazioni sui livelli di isolamento supportati dal driver JDBC, vedere [informazioni sui livelli di isolamento](../../connect/jdbc/understanding-isolation-levels.md).  
  
 Le applicazioni devono controllare le transazioni tramite istruzioni Transact-SQL o i metodi forniti dal driver JDBC, ma non entrambi. L'utilizzo simultaneo di istruzioni Transact-SQL e dei metodi dell'API di JDBC nella stessa transazione potrebbe comportare problemi, tra cui l'impossibilità di eseguire il commit di una transazione quando previsto, oppure l'esecuzione del commit o del rollback di una transazione e l'avvio imprevisto di una nuova transazione oppure il verificarsi di eccezioni di tipo "Impossibile riprendere la transazione".  
  
## <a name="using-local-transactions"></a>Utilizzo delle transazioni locali  
 Una transazione viene considerata locale se è a fase singola e viene gestita direttamente dal database. Il driver JDBC supporta le transazioni locali utilizzando diversi metodi del [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe, inclusi [setAutoCommit](../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md), [commit](../../connect/jdbc/reference/commit-method-sqlserverconnection.md)e [rollback](../../connect/jdbc/reference/rollback-method.md). Le transazioni locali vengono in genere gestite in modo esplicito dall'applicazione o in modo automatico dal server applicazioni Java Platform, Enterprise Edition (Java EE).  
  
 Nell'esempio seguente viene eseguita una transazione locale costituita da due istruzioni separate nel `try` blocco. Le istruzioni vengono eseguite sulla tabella Production. ScrapReason nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio e viene eseguito se non vengono generate eccezioni. Il codice di `catch` blocco rollback della transazione se viene generata un'eccezione.  
  
 [!code[JDBC#UnderstandingTransactions1](../../connect/jdbc/codesnippet/Java/understanding-transactions_1.java)]  
  
## <a name="using-distributed-transactions"></a>Utilizzo di transazioni distribuite  
 Una transazione distribuita aggiorna dati su due o più database in rete conservando al contempo le importanti caratteristiche di atomicità, consistenza, isolamento e durata, ovvero le proprietà ACID, dell'elaborazione delle transazioni. Il supporto delle transazioni distribuite è stato aggiunto all'API JDBC nella specifica JDBC 2.0 Optional API. La gestione delle transazioni distribuite viene in genere eseguita automaticamente dalla gestione transazioni JTS (Java Transaction Service) in un ambiente server applicazioni Java EE. Tuttavia, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta le transazioni distribuite con qualsiasi gestione transazioni conforme API JTA (Java Transaction).  
  
 Il driver JDBC si integra perfettamente con [!INCLUDE[msCoName](../../includes/msconame_md.md)] distribuita di Distributed Transaction Coordinator (MS DTC) per fornire un reale supporto delle transazioni con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. MS DTC è una funzionalità delle transazioni distribuite fornita da [!INCLUDE[msCoName](../../includes/msconame_md.md)] per [!INCLUDE[msCoName](../../includes/msconame_md.md)] sistemi Windows. MS DTC utilizza l'elaborazione delle transazioni si basa sulla collaudata tecnologia di [!INCLUDE[msCoName](../../includes/msconame_md.md)] per supportare caratteristiche XA quali il protocollo completo di commit distribuito e il recupero delle transazioni distribuite.  
  
 Per ulteriori informazioni su come usare transazioni distribuite, vedere [nozioni fondamentali sulle transazioni XA](../../connect/jdbc/understanding-xa-transactions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni con il driver JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
