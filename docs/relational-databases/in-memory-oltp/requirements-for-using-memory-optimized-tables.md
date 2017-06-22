---
title: Requisiti per l'uso di tabelle con ottimizzazione per la memoria | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 11/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47d9a7e8-c597-4b95-a58a-dcf66df8e572
caps.latest.revision: 65
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d30c5b808c13258e784187182eab23b0a50c76e0
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="requirements-for-using-memory-optimized-tables"></a>Requisiti per l'utilizzo di tabelle con ottimizzazione per la memoria
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Per l'uso di OLTP in memoria nel database di Azure, vedere [Introduzione alle tecnologie in memoria (anteprima) in database SQL](http://azure.microsoft.com/documentation/articles/sql-database-in-memory/).  
  
 In aggiunta ai requisiti indicati in [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md), per usare OLTP in memoria sono necessari i requisiti seguenti:  
  
-   SQL Server 2016 SP1 o versione successiva, qualsiasi edizione. Per SQL Server 2014 ed SQL Server 2016 RTM (pre-SP1) sono necessarie le edizioni Enterprise, Developer o Evaluation.
    - Nota: OLTP in memoria richiede la versione di SQL Server a 64 bit.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiede memoria sufficiente per contenere i dati in tabelle con ottimizzazione per la memoria e indici, nonché memoria aggiuntiva per supportare il carico di lavoro in linea. Per altre informazioni, vedere [Stimare i requisiti di memoria delle tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md) .  

-   Quando si esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in una macchina virtuale (VM), assicurarsi che la memoria allocata alla macchina virtuale sia sufficiente per supportare la memoria necessaria per gli indici e le tabelle con ottimizzazione per la memoria. A seconda dell'applicazione host della macchina virtuale, l'opzione di configurazione per garantire l'allocazione di memoria per la macchina virtuale può essere chiamata prenotazione di memoria oppure, se viene usata la memoria dinamica, RAM minima. Assicurarsi che queste impostazioni siano sufficienti per soddisfare le esigenze dei database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
-   Liberare una quantità di spazio su disco corrispondente al doppio delle dimensioni delle tabelle con ottimizzazione per la memoria durevoli.  
  
-   Un processore deve supportare l'istruzione **cmpxchg16b** per l'uso di OLTP in memoria. Tutti i moderni processori a 64 bit supportano **cmpxchg16b**.  
  
     Se si usa una macchina virtuale e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] visualizza un errore causato da un processore di versione precedente, controllare se l'applicazione host della macchina virtuale include un'opzione di configurazione che consente l'uso di **cmpxchg16b**. In caso contrario, è possibile usare Hyper-, che supporta **cmpxchg16b** senza dover modificare l'opzione di configurazione.  
  
-   OLTP in memoria viene installato come parte dei **servizi del motore di database**.  
  
     Per installare la generazione del report ([Determinare se una tabella o una stored procedure deve essere trasferita a OLTP in memoria](../../relational-databases/in-memory-oltp/determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)) e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (per gestire OLTP In memoria tramite Esplora oggetti [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ), [scaricare SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).  
  
## <a name="important-notes-on-using-includehek2includeshek-2-mdmd"></a>Note importanti sull'uso di [!INCLUDE[hek_2](../../includes/hek-2-md.md)]  
  
-   A partire da SQL Server 2016 non esiste alcun limite alle dimensioni delle tabelle con ottimizzazione per la memoria, ad eccezione della memoria disponibile. In SQL Server 2014 le dimensioni totali in memoria di tutte le tabelle durevoli di un database non devono superare i 250 GB per i database di SQL Server 2014. Per altre informazioni, vedere [Stimare i requisiti di memoria delle tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/estimate-memory-requirements-for-memory-optimized-tables.md).  
    - Nota: a partire da SQL Server 2016 SP1, le edizioni Standard ed Express supportano OLTP in memoria, ma impongono quote sulla quantità di memoria che è possibile usare per le tabelle con ottimizzazione per la memoria in un database specifico. Nell'edizione Standard tale quota è di 32 GB per ogni database; nell'edizione Express è di 352 MB per ogni database. 
  
-   Se si crea uno o più database con tabelle con ottimizzazione per la memoria, è consigliabile abilitare l'inizializzazione immediata dei file per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Per eseguire tale operazione è necessario concedere all'account di avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il diritto utente SE_MANAGE_VOLUME_NAME. Senza l'inizializzazione immediata dei file, i file di archiviazione con ottimizzazione per la memoria (file di dati e differenziali) vengono inizializzati al momento della creazione. Tale operazione può causare una riduzione delle prestazioni del carico di lavoro. Per altre informazioni sull'inizializzazione immediata dei file, vedere [Inizializzazione di file di database](http://msdn.microsoft.com/library/ms175935\(SQL.105\).aspx). Per informazioni su come abilitare l'inizializzazione immediata dei file, vedere l'argomento relativo ai [motivi e alle modalità di abilitazione dell'inizializzazione immediata dei file](http://blogs.msdn.com/b/sql_pfe_blog/archive/2009/12/23/how-and-why-to-enable-instant-file-initialization.aspx).  
  
## <a name="see-also"></a>Vedere anche  
 [OLTP in memoria &#40;ottimizzazione per la memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

