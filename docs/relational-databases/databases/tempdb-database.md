---
title: Database tempdb | Microsoft Docs
ms.custom: 
ms.date: 03/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
caps.latest.revision: "66"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.openlocfilehash: 003196d8c30ca45c54750587c03c8d7d6e5a358d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="tempdb-database"></a>Database tempdb
  Il database di sistema **tempdb** è una risorsa globale disponibile a tutti gli utenti connessi all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e viene usata per contenere gli elementi seguenti:  
  
-   Oggetti utente temporanei creati in modo esplicito, ad esempio tabelle temporanee globali o locali, stored procedure temporanee, variabili di tabella o cursori.  
  
-   Oggetti interni creati dal [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], ad esempio tabelle di lavoro in cui archiviare i risultati intermedi delle operazioni di spooling o di ordinamento.  
  
-   Versioni di riga generate dalle transazioni di modifica dei dati in un database in cui viene usato il Read committed tramite isolamento del controllo delle versioni delle righe o transazioni di isolamento dello snapshot.  
  
-   Versioni di riga generate dalle transazioni di modifica dei dati per le caratteristiche, ad esempio le operazioni sugli indici online, la caratteristica MARS (Multiple Active Result Set) e i trigger AFTER.  
  
 In **tempdb** viene registrato un numero minimo di operazioni Consente il rollback delle transazioni. **tempdb** viene ricreato ogni volta che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene avviato in modo che il sistema inizi sempre con una copia pulita del database. Poiché le tabelle e le stored procedure temporanee vengono eliminate automaticamente al momento della disconnessione e poiché al momento della chiusura del sistema non vi sono connessioni attive, nessuna parte del database **tempdb** viene salvata per le sessioni successive di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le operazioni di backup e di ripristino non sono consentite nel database **tempdb**.  
  
## <a name="physical-properties-of-tempdb"></a>Proprietà fisiche di tempdb  
 Nella tabella seguente sono elencati i valori iniziali di configurazione dei dati e dei file di log di **tempdb** . Le dimensioni di questi file possono variare leggermente a seconda dell'edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|File|Nome logico|Nome fisico|Dimensioni iniziali|Aumento di dimensioni del file|  
|----------|------------------|-------------------|------------------|-----------------|  
|Dati primari|tempdev|tempdb.mdf|8 megabyte|Aumento automatico di 64 MB fino a quando il disco risulta pieno|  
|File di dati secondari*|temp#|tempdb_mssql_#.ndf|8 megabyte|Aumento automatico di 64 MB fino a quando il disco risulta pieno|  
|File di log|templog|templog.ldf|8 megabyte|Aumento automatico di 64 megabyte fino a un massimo di 2 terabyte|  
  
 \* Il numero di file dipende dal numero di core (logici) del computer. Il valore sarà il numero di core o 8, a seconda di quale sia il valore inferiore.   
Il valore predefinito per il numero di file di dati si basa sulle linee guida generali in [KB 2154845](https://support.microsoft.com/en-us/kb/2154845/).  
  
## <a name="performance-improvements-in-tempdb"></a>Miglioramenti delle prestazioni in tempdb  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]le prestazioni di **tempdb** sono state migliorate come segue:  
  
-   È possibile memorizzare nella cache tabelle temporanee e variabili di tabella. La memorizzazione nella cache consente di eseguire molto rapidamente le operazioni di eliminazione e creazione degli oggetti temporanei e di ridurre i problemi di contesa nell'allocazione delle pagine.  
  
-   Il protocollo di latch delle pagine di allocazione è stato migliorato. In questo modo è possibile ridurre il numero di latch di aggiornamento (UP) usati.  
  
-   L'overhead di registrazione per il database **tempdb** è stato ridotto. In questo modo si riduce l'utilizzo di banda per operazioni di I/O su disco nel file di log di **tempdb** .  
  
-   Durante l'installazione di una nuova istanza vengono aggiunti più file di dati di tempdb. Questa attività può essere eseguita con un nuovo controllo input dell'interfaccia utente nella sezione **Configurazione del motore di database** e con un parametro della riga di comando /SQLTEMPDBFILECOUNT. Per impostazione predefinita, il programma di installazione aggiunge un numero di file tempdb pari al numero di CPU oppure a 8, a seconda di quale sia il valore inferiore.  
  
-   Se ci sono più file di dati **tempdb** , le dimensioni di tutti i file aumenteranno contemporaneamente e della stessa quantità in base alle impostazioni specificate.  Il flag di traccia 1117 non è più richiesto.  
  
-   Tutte le allocazioni in **tempdb** usano extent uniformi. Il flag di traccia 1118 non è più richiesto.  
  
-   Per il filegroup primario, la proprietà AUTOGROW_ALL_FILES è attivata e non può essere modificata.  
  
### <a name="moving-the-tempdb-data-and-log-files"></a>Spostamento dei dati e dei file di log di tempdb  
 Per spostare i file di log e i dati **tempdb** , vedere [Spostare i database di sistema](../../relational-databases/databases/move-system-databases.md).  
  
### <a name="database-options"></a>Opzioni di database  
 Nella tabella seguente sono elencati i valori predefiniti delle singole opzioni di database di **tempdb** e viene indicato se l'opzione è modificabile. Per visualizzare le impostazioni correnti di queste opzioni, usare la vista del catalogo [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) .  
  
|Opzione di database|Valore predefinito|Modificabile|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|Sì|  
|ANSI_NULL_DEFAULT|OFF|Sì|  
|ANSI_NULLS|OFF|Sì|  
|ANSI_PADDING|OFF|Sì|  
|ANSI_WARNINGS|OFF|Sì|  
|ARITHABORT|OFF|Sì|  
|AUTO_CLOSE|OFF|No|  
|AUTO_CREATE_STATISTICS|ON|Sì|  
|AUTO_SHRINK|OFF|No|  
|AUTO_UPDATE_STATISTICS|ON|Sì|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|Sì|  
|CHANGE_TRACKING|OFF|No|  
|CONCAT_NULL_YIELDS_NULL|OFF|Sì|  
|CURSOR_CLOSE_ON_COMMIT|OFF|Sì|  
|CURSOR_DEFAULT|GLOBAL|Sì|  
|Opzioni relative alla disponibilità del database|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|No<br /><br /> No<br /><br /> No|  
|DATE_CORRELATION_OPTIMIZATION|OFF|Sì|  
|DB_CHAINING|ON|No|  
|ENCRYPTION|OFF|No|  
|MIXED_PAGE_ALLOCATION|OFF|No|  
|NUMERIC_ROUNDABORT|OFF|Sì|  
|PAGE_VERIFY|CHECKSUM per nuove installazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NONE per aggiornamenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|Sì|  
|PARAMETERIZATION|SIMPLE|Sì|  
|QUOTED_IDENTIFIER|OFF|Sì|  
|READ_COMMITTED_SNAPSHOT|OFF|No|  
|RECOVERY|SIMPLE|No|  
|RECURSIVE_TRIGGERS|OFF|Sì|  
|Opzioni relative a Service Broker|ENABLE_BROKER|Sì|  
|TRUSTWORTHY|OFF|No|  
  
 Per una descrizione di queste opzioni di database, vedere [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="restrictions"></a>Restrizioni  
 Di seguito sono riportate le operazioni che non è possibile eseguire sul database **tempdb** :  
  
-   Aggiunta di filegroup.  
  
-   Backup o ripristino del database.  
  
-   Modifica delle regole di confronto. Le regole di confronto predefinite corrispondono a quelle del server.  
  
-   Modifica del proprietario del database. **tempdb** è di proprietà di **sa**.  
  
-   Creazione di uno snapshot del database.  
  
-   Eliminazione del database.  
  
-   Eliminazione dell'utente **guest** dal database.  
  
-   Abilitazione dell'acquisizione dei dati delle modifiche.  
  
-   Partecipazione al mirroring del database.  
  
-   Rimozione del filegroup primario, del file di dati primario o del file di log.  
  
-   Ridenominazione del filegroup primario o del database.  
  
-   Esecuzione di DBCC CHECKALLOC.  
  
-   Esecuzione di DBCC CHECKCATALOG.  
  
-   Impostazione del database su OFFLINE.  
  
-   Impostazione del database o del filegroup primario su READ_ONLY.  
  
## <a name="permissions"></a>Autorizzazioni  
 Qualsiasi utente può creare oggetti temporanei in tempdb. Gli utenti possono accedere solo ai propri oggetti, a meno che non ottengano ulteriori autorizzazioni. È possibile revocare l'autorizzazione per la connessione a tempdb per impedire a un utente di utilizzarlo, tuttavia questa operazione non è consigliabile poiché in alcune operazioni di routine è richiesto l'utilizzo di tempdb.  
  
## <a name="related-content"></a>Contenuto correlato  
 [Opzione SORT_IN_TEMPDB per gli indici](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)  
  
 [Database di sistema.](../../relational-databases/databases/system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
 [Spostare file del database](../../relational-databases/databases/move-database-files.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di tempdb in SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81216)  
  
  
