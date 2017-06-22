---
title: Gestire dimensioni di File di Log delle transazioni | Documenti Microsoft
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-transaction-log
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transaction logs [SQL Server], size management
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 6d75e0e40c5642993cb17b09e421fbfebf40f87a
ms.openlocfilehash: cd1931ef0f77c0a1e31c29833f38c51416e267c8
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="manage-the-size-of-the-transaction-log-file"></a>Gestione delle dimensioni del file di log delle transazioni
In questo argomento viene descritto come monitorare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dimensioni del log delle transazioni, compattare il log delle transazioni, aggiungere o aumentare dimensioni di un file di log delle transazioni, ottimizzare la **tempdb** tasso di aumento delle dimensioni del log delle transazioni e controllare l'aumento di dimensioni di un file di log delle transazioni.  

  ##  <a name="MonitorSpaceUse"></a> Monitoraggio dell'utilizzo dello spazio del log  
Monitorare l'utilizzo dello spazio del log tramite [DBCC SQLPERF (LOGSPACE)](https://docs.microsoft.com/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql). Questo comando restituisce informazioni sulla quantità di spazio del log attualmente usata e indica quando il log delle transazioni deve essere troncato. Per ulteriori informazioni, vedere [DBCC SQLPERF Transact-SQL](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md). Per informazioni sulla dimensione del file di log corrente, la dimensione massima e l'opzione di aumento automatico delle dimensioni per il file, è inoltre possibile utilizzare il **dimensioni**, **max_size**, e **crescita** colonne per i file di log in **Sys. database_files**. Per altre informazioni, vedere [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md).  
  
**Importante** Evitare l'overload del disco del log.  

  
##  <a name="ShrinkSize"></a> Compattare il file di log  
 Per ridurre la dimensione fisica di un file di log fisico, è necessario ridurre il file di log. Ciò è utile quando si è certi che un file di log delle transazioni contiene spazio inutilizzato. È possibile compattare un file di log solo mentre il database è online, e almeno un file di log virtuale è disponibile. In alcuni casi, la compattazione del log potrebbe non essere possibile finché il log non viene troncato.  
  
> [!NOTE]
>  Fattori come una transazione con esecuzione prolungata, che mantiene i file di log virtuali attivi per un lungo periodo di tempo, possono limitare in tutto o in parte la compattazione del log. Per informazioni sui fattori che possono ritardare il troncamento del log, vedere [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
 Il processo di compattazione di un file di log comporta la rimozione di uno o più file di log virtuali che non contengono alcuna parte del log logico, ovvero dei *file di log virtuali inattivi*. Quando si compatta un file di log delle transazioni, i file di log virtuali inattivi vengono rimosse dalla fine del file di log per ridurre il log approssimativamente alle dimensioni di destinazione.  
  
 **Compattare un file di log senza compattare i file di database**  
  
-   [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)  
  
-   [Compattare un file](../../relational-databases/databases/shrink-a-file.md)  
  
 **Monitorare gli eventi di compattazione dei file di log**  
  
-   [Log File Auto Shrink Event Class](../../relational-databases/event-classes/log-file-auto-shrink-event-class.md).  
  
 **Monitorare lo spazio del log**  
  
-   [DBCC SQLPERF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)  
  
-   [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) (Vedere le colonne **size**, **max_size** e **growth** per il file o i file di log).  
  
> [!NOTE]
>  È possibile impostare la compattazione automatica, i file di log. È consigliabile tuttavia evitare di eseguire la compattazione automatica impostando la proprietà del database **autoshrink** su FALSE per impostazione predefinita. Se **autoshrink** viene impostato su TRUE, la compattazione automatica riduce le dimensioni di un file solo quando più del 25 percento dello spazio del file risulta inutilizzato. Il file viene compattato fino a quando la percentuale di spazio inutilizzato nel file non risulta pari al 25 percento oppure fino a quando il file non raggiunge le dimensioni originali, a seconda di quale tra questi due sia il valore maggiore. Per informazioni sulla modifica dell'impostazione della proprietà **autoshrink**, vedere [Visualizzare o modificare le proprietà di un database](../../relational-databases/databases/view-or-change-the-properties-of-a-database.md) (uso della proprietà **Auto Shrink** nella pagina **Opzioni**) o [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md) (uso dell'opzione AUTO_SHRINK).  
  

##  <a name="AddOrEnlarge"></a> Aggiungere o aumentare le dimensioni di un file di log  
 È possibile guadagnare spazio aumentando il file di log esistente, se lo spazio su disco sufficiente, oppure aggiungendo un file di log nel database, in genere in un altro disco.  
  
-   Per aggiungere un file di log al database, utilizzare la clausola ADD LOG FILE dell'istruzione ALTER DATABASE. L'aggiunta di un file di log consente l'aumento delle dimensioni del log.  
  
-   Per aumentare le dimensioni del file di log, utilizzare la clausola MODIFY FILE dell'istruzione ALTER DATABASE, specificando la sintassi SIZE e MAXSIZE. Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
    
  
##  <a name="tempdbOptimize"></a> Ottimizzare le dimensioni del log delle transazioni di tempdb  
 Il riavvio di un'istanza del server riporta il log delle transazioni del database **tempdb** alle dimensioni originali, antecedenti all'aumento automatico delle dimensioni. Questo può comportare una riduzione delle prestazioni del log delle transazioni di **tempdb** . Per evitare tale overhead, è possibile incrementare le dimensioni del log delle transazioni di **tempdb** dopo l'avvio o il riavvio dell'istanza del server. Per altre informazioni, vedere [tempdb Database](../../relational-databases/databases/tempdb-database.md).  
  
  
##  <a name="ControlGrowth"></a> Controllare l'aumento delle dimensioni di un file di log delle transazioni  
 Utilizzare il [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md) istruzione per gestire la crescita di un file di log delle transazioni. Si noti quanto segue:  
  
-   Per modificare le dimensioni del file corrente in unità KB, MB, GB e TB, utilizzare l'opzione SIZE.  
  -   Per modificare l'incremento di crescita, utilizzare l'opzione FILEGROWTH. Il valore 0 indica che l'aumento automatico delle dimensioni è disattivato e non è consentita l'allocazione di spazio aggiuntivo. Anche un piccolo aumento automatico delle dimensioni di un file di log può comportare una riduzione delle prestazioni. È consigliabile specificare un incremento di crescita per un file di log sufficientemente grande da consentire di evitare l'espansione frequente. L'incremento di crescita predefinito pari al 10% è solitamente appropriato.  

Per informazioni sulla modifica della proprietà relativa alla crescita di un file di log, vedere [ALTER DATABASE (Transact-SQL)](https://msdn.microsoft.com/library/ms174269.aspx).  
  
-   Per controllare le dimensioni massime di un file di log in unità KB, MB, GB e TB o per impostare la crescita su UNLIMITED, utilizzare l'opzione MAXSIZE.  
  
  
## <a name="see-also"></a>Vedere anche  
 [BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)   
 [Risolvere i problemi relativi a un Log delle transazioni pieno (errore di SQL Server 9002)](../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
  

