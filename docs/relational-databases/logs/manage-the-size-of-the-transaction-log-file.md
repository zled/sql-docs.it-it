---
title: "Gestione delle dimensioni del file di log delle transazioni | Microsoft Docs"
ms.custom: ""
ms.date: "07/14/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-transaction-log"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "log delle transazioni [SQL Server], gestione delle dimensioni"
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# Gestione delle dimensioni del file di log delle transazioni
In questo argomento sono contenute informazioni sul monitoraggio delle dimensioni di un log delle transazioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sulla relativa compattazione, sull'aumento delle dimensioni di un file di log delle transazioni, sull'ottimizzazione del tasso di aumento del log delle transazioni di **tempdb** e sul controllo dell'aumento delle dimensioni di un file di log delle transazioni.  

  ##  <a name="MonitorSpaceUse"></a> Monitoraggio dell'utilizzo dello spazio del log  
È possibile monitorare l'utilizzo dello spazio del log mediante DBCC SQLPERF (LOGSPACE). Questo comando restituisce informazioni sulla quantità di spazio del log attualmente usata e indica quando il log delle transazioni deve essere troncato. Per altre informazioni, vedere [DBCC SQLPERF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md). Per informazioni sulle dimensioni correnti di un file di log, sulle relative dimensioni massime e sull'opzione di aumento automatico delle dimensioni per il file, è anche possibile usare le colonne **size**, **max_size** e **growth** per il file di log in **sys.database_files**. Per altre informazioni, vedere [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).  
  
**Importante** Evitare l'overload del disco del log.  

  
##  <a name="ShrinkSize"></a> Compattare il file di log  
 Per ridurre la dimensione fisica di un file di log fisico, è necessario ridurre il file di log. Ciò può risultare utile se si è a conoscenza del fatto che un file di log delle transazioni contiene spazio inutilizzato che non sarà necessario. La compattazione di un file di log può essere eseguita solo quando il database è online ed è disponibile almeno un file di log virtuale. In alcuni casi, la compattazione del log potrebbe non essere possibile finché il log non viene troncato.  
  
> [!NOTE]  Fattori come una transazione con esecuzione prolungata, che mantiene i file di log virtuali attivi per un lungo periodo di tempo, possono limitare in tutto o in parte la compattazione del log. Per informazioni sui fattori che possono ritardare il troncamento del log, vedere [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
 Il processo di compattazione di un file di log comporta la rimozione di uno o più file di log virtuali che non contengono alcuna parte del log logico, ovvero dei *file di log virtuali inattivi*. Quando si compatta un file di log delle transazioni, viene rimosso dalla fine del file di log un numero di file di log virtuali inattivi sufficiente a ridurre il log approssimativamente alle dimensioni di destinazione.  
  
 **Compattare un file di log senza compattare i file di database**  
  
-   [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)  
  
-   [Compattare un file](../../relational-databases/databases/shrink-a-file.md)  
  
 **Monitorare gli eventi di compattazione dei file di log**  
  
-   [Log File Auto Shrink Event Class](../../relational-databases/event-classes/log-file-auto-shrink-event-class.md).  
  
 **Monitorare lo spazio del log**  
  
-   [DBCC SQLPERF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)  
  
-   [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) (Vedere le colonne **size**, **max_size** e **growth** per il file o i file di log).  
  
> [!NOTE]  La compattazione dei file di log e di database può essere impostata in modo da essere eseguita automaticamente. È consigliabile tuttavia evitare di eseguire la compattazione automatica impostando la proprietà del database **autoshrink** su FALSE per impostazione predefinita. Se **autoshrink** viene impostato su TRUE, la compattazione automatica riduce le dimensioni di un file solo quando più del 25 percento dello spazio del file risulta inutilizzato. Il file viene compattato fino a quando la percentuale di spazio inutilizzato nel file non risulta pari al 25 percento oppure fino a quando il file non raggiunge le dimensioni originali, a seconda di quale tra questi due sia il valore maggiore. Per informazioni sulla modifica dell'impostazione della proprietà **autoshrink**, vedere [Visualizzare o modificare le proprietà di un database](../../relational-databases/databases/view-or-change-the-properties-of-a-database.md) (uso della proprietà **Auto Shrink** nella pagina **Opzioni**) o [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md) (uso dell'opzione AUTO_SHRINK).  
  

##  <a name="AddOrEnlarge"></a> Aggiungere o aumentare le dimensioni di un file di log  
 In alternativa, è possibile guadagnare spazio aumentando le dimensioni del file di log esistente, se lo spazio è sufficiente, oppure aggiungendo un file di log al database, in genere in un disco diverso.  
  
-   Per aggiungere un file di log al database, utilizzare la clausola ADD LOG FILE dell'istruzione ALTER DATABASE. L'aggiunta di un file di log consente l'aumento delle dimensioni del log.  
  
-   Per aumentare le dimensioni del file di log, utilizzare la clausola MODIFY FILE dell'istruzione ALTER DATABASE, specificando la sintassi SIZE e MAXSIZE. Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
    
  
##  <a name="tempdbOptimize"></a> Ottimizzare le dimensioni del log delle transazioni di tempdb  
 Il riavvio di un'istanza del server riporta il log delle transazioni del database **tempdb** alle dimensioni originali, antecedenti all'aumento automatico delle dimensioni. Questo può comportare una riduzione delle prestazioni del log delle transazioni di **tempdb** . Per evitare tale overhead, è possibile incrementare le dimensioni del log delle transazioni di **tempdb** dopo l'avvio o il riavvio dell'istanza del server. Per altre informazioni, vedere [tempdb Database](../../relational-databases/databases/tempdb-database.md).  
  
  
##  <a name="ControlGrowth"></a> Controllare l'aumento delle dimensioni di un file di log delle transazioni  
 È possibile usare l'istruzione [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md) per gestire la crescita di un file di log delle transazioni. Si noti quanto segue:  
  
-   Per modificare le dimensioni del file corrente in unità KB, MB, GB e TB, utilizzare l'opzione SIZE.  
  -   Per modificare l'incremento di crescita, utilizzare l'opzione FILEGROWTH. Il valore 0 indica che l'aumento automatico delle dimensioni è disattivato e non è consentita l'allocazione di spazio aggiuntivo. Anche un piccolo aumento automatico delle dimensioni di un file di log può comportare una riduzione delle prestazioni. È consigliabile specificare un incremento di crescita per un file di log sufficientemente grande da consentire di evitare l'espansione frequente. L'incremento di crescita predefinito pari al 10% è solitamente appropriato.  

Per informazioni sulla modifica della proprietà relativa alla crescita di un file di log, vedere [ALTER DATABASE (Transact-SQL)](https://msdn.microsoft.com/library/ms174269.aspx).  
  
-   Per controllare le dimensioni massime di un file di log in unità KB, MB, GB e TB o per impostare la crescita su UNLIMITED, utilizzare l'opzione MAXSIZE.  
  
  
## Vedere anche  
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Risolvere i problemi relativi a un log delle transazioni completo &#40;Errore di SQL Server 9002&#41;](../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
  