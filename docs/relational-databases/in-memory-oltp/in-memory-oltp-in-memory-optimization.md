---
title: "OLTP in memoria (ottimizzazione per la memoria) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OLTP in memoria"
  - "Tabelle con ottimizzazione per la memoria"
ms.assetid: e1d03d74-2572-4a55-afd6-7edf0bc28bdb
caps.latest.revision: 106
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 105
---
# OLTP in memoria (ottimizzazione per la memoria)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] può migliorare significativamente le prestazioni di elaborazione delle transazioni, di inserimento e caricamento dei dati e di scenari di dati temporanei.  Per ottenere il codice di base e le informazioni necessarie per verificare rapidamente la tabella con ottimizzazione per la memoria e la stored procedure compilata in modo nativo, vedere
 -  [Avvio rapido 1: Tecnologie OLTP in memoria per migliorare le prestazioni di Transact-SQL](../../relational-databases/in-memory-oltp/quick-start-1-in-memory-oltp-technologies-for-faster-transact-sql-performance.md)  
 
Video di 17 minuti che descrive OLTP in memoria e i vantaggi per le prestazioni:

-  [In-Memory OLTP in SQL Server 2016](https://www.youtube.com/watch?v=l5l5eophmK4) (OLTP in memoria in SQL Server 2016)

Per scaricare la demo sulle prestazioni per OLTP in memoria usata nel video: 

- [In-Memory OLTP Performance Demo v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0) (Demo sulle prestazioni di OLTP in memoria v1.0)

Per una panoramica più dettagliata di OLTP in memoria e un'analisi degli scenari che esaminano i vantaggi derivanti dalla tecnologia per le prestazioni:

- [Panoramica e scenari di utilizzo](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)
 
 Si noti che [!INCLUDE[hek_2](../../includes/hek-2-md.md)] è la tecnologia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per migliorare le prestazioni dell'elaborazione delle transazioni. Per la tecnologia di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che migliora la creazione di report e le prestazioni di query di analisi, vedere [Guida agli indici columnstore](../Topic/Columnstore%20Indexes%20Guide.md).
  
 Sono stati apportati diversi miglioramenti a OLTP in memoria in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e in [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]. La superficie di attacco Transact-SQL è stata aumentata per semplificare la migrazione delle applicazioni di database. È stato aggiunto il supporto per l'esecuzione di operazioni ALTER per le tabelle con ottimizzazione per la memoria e le stored procedure compilate in modo nativo per semplificare la gestione delle applicazioni. Per informazioni sulle nuove funzionalità in [!INCLUDE[hek_2](../../includes/hek-2-md.md)], vedere [Novità del motore di database](../Topic/What's%20New%20in%20Database%20Engine.md).  
  
> [!NOTE]  
>  **Per provarlo**  
>   
>  OLTP in memoria è disponibile nei database SQL di Azure Premium. Per iniziare a usare OLTP in memoria nonché columnstore nel database SQL di Azure, vedere [Introduzione alle tecnologie in memoria (anteprima) in database SQL](https://azure.microsoft.com/documentation/articles/sql-database-in-memory/).  
  

## <a name="in-this-section"></a>Contenuto della sezione  
 In questa sezione vengono trattati gli argomenti seguenti:  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Avvio rapido 1: Tecnologie OLTP in memoria per migliorare le prestazioni di Transact-SQL](../../relational-databases/in-memory-oltp/quick-start-1-in-memory-oltp-technologies-for-faster-transact-sql-performance.md)|Analizza in maniera approfondita OLTP in memoria|
|[Panoramica e scenari di utilizzo](../../relational-databases/in-memory-oltp/overview-and-usage-scenarios.md)|Panoramica delle informazioni su OLTP in memoria e degli scenari che ne esaminano i vantaggi.|
|[Requisiti per l'utilizzo di tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/requirements-for-using-memory-optimized-tables.md)|Vengono descritti i requisiti hardware e software e le linee guida per l'utilizzo di tabelle con ottimizzazione per la memoria.|  
|[Esempi di codice di OLTP in memoria](../../relational-databases/in-memory-oltp/in-memory-oltp-code-samples.md)|Sono contenuti esempi di codice che illustrano come creare e usare una tabella con ottimizzazione per la memoria.|  
|[Tabelle con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/memory-optimized-tables.md)|Vengono introdotte le tabelle con ottimizzazione per la memoria.|  
|[Variabili di tabella con ottimizzazione per la memoria](../Topic/Memory-Optimized%20Table%20Variables.md)|Esempio di codice in cui viene mostrato come usare una variabile di tabella con ottimizzazione per la memoria anziché una variabile di tabella tradizionale per ridurre l'utilizzo di tempdb.|  
|[Indici in tabelle con ottimizzazione per la memoria](../Topic/Indexes%20on%20Memory-Optimized%20Tables.md)|Vengono introdotti indici con ottimizzazione per la memoria.|  
|[Stored procedure compilate in modo nativo](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)|Vengono illustrate le stored procedure compilate in modo nativo.|  
|[Gestione della memoria per OLTP in memoria](../Topic/Managing%20Memory%20for%20In-Memory%20OLTP.md)|Informazioni e gestione dell'utilizzo della memoria nel sistema.|  
|[Creazione e gestione dell'archiviazione per gli oggetti con ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)|Vengono illustrati i file di dati e differenziali in cui vengono archiviate le informazioni sulle transazioni nelle tabelle con ottimizzazione per la memoria.|  
|[Eseguire il backup, ripristinare e recuperare tabelle con ottimizzazione per la memoria](../Topic/Backup,%20Restore,%20and%20Recovery%20of%20Memory-Optimized%20Tables.md)|Descrive le operazioni di backup, ripristino e recupero delle tabelle con ottimizzazione per la memoria.|  
|[Supporto di Transact-SQL per OLTP in memoria](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)|Descrive il supporto di [!INCLUDE[tsql](../../includes/tsql-md.md)] per [!INCLUDE[hek_2](../../includes/hek-2-md.md)].|  
|[Supporto della disponibilità elevata per i database OLTP in memoria](../../relational-databases/in-memory-oltp/high-availability-support-for-in-memory-oltp-databases.md)|Descrive i gruppi di disponibilità e il clustering di failover in [!INCLUDE[hek_2](../../includes/hek-2-md.md)].|  
|[Supporto di SQL Server per OLTP in memoria](../../relational-databases/in-memory-oltp/sql-server-support-for-in-memory-oltp.md)|Elenco della sintassi e delle funzionalità nuove e aggiornate per il supporto di tabelle con ottimizzazione per la memoria.|  
|[Migrazione a OLTP in memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)|Viene illustrato come eseguire la migrazione di tabelle basate su disco in tabelle con ottimizzazione per la memoria.|  
  
 Altre informazioni su [!INCLUDE[hek_2](../../includes/hek-2-md.md)] sono disponibili in:  

- [Video che descrive OLTP in memoria e i vantaggi per le prestazioni](https://www.youtube.com/watch?v=l5l5eophmK4).

- [In-Memory OLTP Performance Demo v1.0](https://github.com/Microsoft/sql-server-samples/releases/tag/in-memory-oltp-demo-v1.0) (Demo sulle prestazioni di OLTP in memoria v1.0)

-   [White paper tecnico su OLTP in memoria di SQL Server](https://msdn.microsoft.com/library/mt764316.aspx)  

-   [Confronto tra le funzionalità di OLTP in memoria di SQL Server e columnstore](http://download.microsoft.com/download/D/0/0/D0075580-6D72-403D-8B4D-C3BD88D58CE4/SQL_Server_2016_In_Memory_OLTP_and_Columnstore_Comparison_White_Paper.pdf)

-   Novità di OLTP in memoria di SQL Server 2016 [Parte 1](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/11/12/in-memory-oltp-whats-new-in-sql2016-ctp3/) e [Parte 2](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/25/whats-new-for-in-memory-oltp-in-sql-server-2016-since-ctp3/)
  
-   [OLTP in memoria: considerazioni sulla migrazione e sui modelli di carico di lavoro comuni](http://msdn.microsoft.com/library/dn673538.aspx)  
  
-   [Blog di OLTP in memoria](http://go.microsoft.com/fwlink/?LinkId=311696)  
  
## <a name="see-also"></a>Vedere anche  
 [Caratteristiche del database](../../relational-databases/database-features.md)  
  
  