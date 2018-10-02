---
title: DBCC SHRINKFILE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SHRINKFILE
- DBCC_SHRINKFILE_TSQL
- DBCC SHRINKFILE
- SHRINKFILE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data shrinking [SQL Server]
- TRUNCATEONLY option
- shrinking files
- NOTRUNCATE option
- shrinking databases
- decreasing database size
- file shrinking [SQL Server]
- database shrinking [SQL Server]
- logs [SQL Server], shrinking
- reducing database size
- DBCC SHRINKFILE statement
ms.assetid: e02b2318-bee9-4d84-a61f-2fddcf268c9f
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: ef14c1ab455776da142993dd4103cc5a42921848
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600821"
---
# <a name="dbcc-shrinkfile-transact-sql"></a>DBCC SHRINKFILE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Compatta le dimensioni del file di dati o di log specificato per il database corrente o svuota un file spostando i dati dal file specificato ad altri file dello stesso filegroup, consentendo la rimozione del file dal database. È possibile compattare un file fino a dimensioni inferiori rispetto a quelle specificate al momento della creazione. Le dimensioni minime del file verranno reimpostate sul nuovo valore.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
  
DBCC SHRINKFILE   
(  
    { file_name | file_id }   
    { [ , EMPTYFILE ]   
    | [ [ , target_size ] [ , { NOTRUNCATE | TRUNCATEONLY } ] ]  
    }  
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
*file_name*  
Nome logico del file che si desidera compattare.
  
*file_id*  
Numero di identificazione (ID) del file che si desidera compattare. Per ottenere un ID file, usare la funzione di sistema [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) o eseguire una query sulla vista del catalogo [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) nel database corrente.
  
*target_size*  
Dimensioni del file, in megabyte, espresse come valore di tipo integer. Se questo argomento viene omesso, il file viene compattato in base alle dimensioni di file predefinite. Le dimensioni predefinite sono quelle specificate al momento della creazione del file.
  
> [!NOTE]  
>  È possibile ridurre le dimensioni predefinite di un file vuoto usando DBCC SHRINKFILE *target_size*. Se si crea ad esempio un file con dimensioni pari a 5 MB e si riducono le dimensioni a 3 MB mentre il file è ancora vuoto, le dimensioni predefinite vengono impostate su 3 Mb. Questa condizione si applica solo a file vuoti in cui non sono mai stati contenuti dati.  
  
Questa opzione non è supportata per i contenitori del filegroup FILESTREAM.  
Se viene specificato *target_size*, l'istruzione DBCC SHRINKFILE tenta di compattare il file fino alle dimensioni specificate. Le pagine utilizzate nella sezione di file che si desidera rendere disponibile vengono rilocate nello spazio disponibile nella sezione di file mantenuta. Nel caso di un file di dati di 10 MB, ad esempio, un'operazione DBCC SHRINKFILE con l'argomento *target_size* impostato su 8 comporta la riallocazione di tutte le pagine usate negli ultimi 2 MB del file in qualsiasi pagina non allocata nei primi 8 MB del file. L'istruzione DBCC SHRINKFILE non compatta un file oltre le dimensioni necessarie per l'archiviazione dei dati nel file. Se, ad esempio, vengono usati 7 MB di un file di dati di 10 MB, un'istruzione DBCC SHRINKFILE con l'argomento *target_size* impostato su 6 compatta il file fino a 7 MB, non 6 MB.
  
EMPTYFILE  
Esegue la migrazione di tutti i dati dal file specificato in altri file dello **stesso filegroup**. In altre parole, EmptyFile esegue la migrazione dei dati dal file specificato in altri file presenti nello stesso filegroup. Emptyfile garantisce che al file non verranno aggiunti nuovi dati, sebbene non sia contrassegnato come di sola lettura. È possibile rimuovere il file usando l'istruzione [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md). Se la dimensione del file viene modificata tramite l'istruzione [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md), il flag di sola lettura viene reimpostato e i dati possono essere aggiunti.

Per i contenitori del filegroup FILESTREAM, non è possibile rimuovere il file utilizzando ALTER DATABASE finché il Garbage Collector per FILESTREAM non ha eseguito ed eliminato tutti i contenitori del filegroup non necessari che EMPTYFILE ha copiato in un altro contenitore. Per altre informazioni, vedere [sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  
> [!NOTE]  
>  Per informazioni sulla rimozione di un contenitore FILESTREAM, vedere la sezione corrispondente in [Opzioni per file e filegroup ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)  
  
NOTRUNCATE  
Sposta le pagine allocate dalla fine di un file di dati a pagine non allocate all'inizio del file specificando o meno *target_percent*. Lo spazio disponibile alla fine del file non viene restituito al sistema operativo e le dimensioni fisiche del file rimangono invariate. Pertanto, quando si specifica NOTRUNCATE, sembra che il file non venga compattato.
NOTRUNCATE è applicabile solo ai file di dati. I file di log non sono interessati.   Questa opzione non è supportata per i contenitori del filegroup FILESTREAM.
  
TRUNCATEONLY  
Rilascia tutto lo spazio disponibile alla fine del file al sistema operativo senza eseguire alcuno spostamento di pagine all'interno del file. Il file di dati viene compattato solo fino all'ultimo extent allocato.
*target_size* viene ignorato se specificato con TRUNCATEONLY.  
L'opzione TRUNCATEONLY non sposta le informazioni nel log, ma rimuove i VLF inattivi dalla fine del file di log. Questa opzione non è supportata per i contenitori del filegroup FILESTREAM.
  
WITH NO_INFOMSGS  
Disattiva tutti i messaggi informativi.
  
## <a name="result-sets"></a>Set di risultati  
Nella tabella seguente vengono descritte le colonne del set di risultati.
  
|Nome colonna|Descrizione|  
|---|---|
|**DbId**|Numero di identificazione del database del file che [!INCLUDE[ssDE](../../includes/ssde-md.md)] tenta di compattare.|  
|**FileId**|Numero di identificazione del file che [!INCLUDE[ssDE](../../includes/ssde-md.md)] tenta di compattare.|  
|**CurrentSize**|Numero di pagine da 8 KB attualmente occupate dal file.|  
|**MinimumSize**|Numero minimo di pagine da 8 KB che il file può occupare. Corrisponde alle dimensioni minime o alle dimensioni originali di un file.|  
|**UsedPages**|Numero di pagine da 8 KB utilizzate dal file.|  
|**EstimatedPages**|Numero di pagine da 8 KB calcolato da [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Corrisponde alle possibili dimensioni finali del file compattato.|  
  
## <a name="remarks"></a>Remarks  
L'istruzione DBCC SHRINKFILE viene applicata ai file del database corrente. Per altre informazioni su come modificare il database corrente, vedere [USE &#40;Transact-SQL&#41;](../../t-sql/language-elements/use-transact-sql.md).
  
Le operazioni di DBCC SHRINKFILE possono essere arrestate in qualsiasi fase del processo. Il lavoro completato fino a quel momento viene mantenuto. Se si usa il parametro EMPTYFILE per un file e l'operazione viene annullata, il file non viene contrassegnato per impedire l'aggiunta di altri dati.
  
Quando un'operazione DBCC SHRINKFILE ha esito negativo, viene generato un errore.
  
 Non è necessario che il database da compattare sia in modalità utente singolo. Durante la fase di compattazione del file, il database può essere utilizzato da altri utenti. Per la compattazione dei database di sistema, non è necessario eseguire l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in modalità utente singolo.  
  
## <a name="shrinking-a-log-file"></a>Compattazione di un file di log  
Per i file di log, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] usa *target_size* per calcolare la dimensione di destinazione dell'intero log; di conseguenza, *target_size* è la quantità di spazio disponibile nel log dopo l'operazione di compattazione. Le dimensioni di destinazione per l'intero log vengono quindi convertite nelle dimensioni di destinazione per ogni file di log. DBCC SHRINKFILE tenta di compattare immediatamente ogni file di log fisico fino alle dimensioni di destinazione specificate. Se invece i log virtuali includono parti del log logico oltre le dimensioni di destinazione, [!INCLUDE[ssDE](../../includes/ssde-md.md)] libera la maggior quantità di spazio possibile e viene visualizzato un messaggio informativo in cui sono descritte le operazioni necessarie per estrarre le parti del log logico dai log virtuali alla fine del file. Dopo l'esecuzione di queste azioni, è possibile utilizzare DBCC SHRINKFILE per liberare lo spazio rimanente.
  
Poiché è possibile compattare un file di log solo fino al limite del file di log virtuale, potrebbe essere impossibile compattare un file di log fino a ottenere dimensioni inferiori rispetto a quelle del file di log virtuale, anche se non viene utilizzato. Le dimensioni del file di log virtuale vengono scelte in modo dinamico da [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante la creazione o l'estensione dei file di log.
  
## <a name="best-practices"></a>Procedure consigliate  
Quando si pianifica la compattazione di un file, considerare le informazioni seguenti:
-   Un'operazione di compattazione è più efficace dopo l'esecuzione di un'operazione che crea una quantità elevata di spazio inutilizzato, ad esempio il troncamento o l'eliminazione di una tabella.  
-   La maggior parte dei database richiede spazio disponibile per lo svolgimento delle normali attività quotidiane. Se si compatta ripetutamente un database ma le sue dimensioni aumentano di nuovo significa che lo spazio compattato è necessario per le normali operazioni. In questi casi è inutile compattare ripetutamente il database.  
-   L'operazione di compattazione generalmente aumenta la frammentazione degli indici del database. Questo è un ulteriore motivo per evitare di compattare ripetutamente un database.  
-   Compattare più file nello stesso database in sequenza anziché contemporaneamente. La contesa sulle tabelle di sistema può provocare ritardi a causa del blocco.  
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
In questa sezione viene descritto come diagnosticare e correggere eventuali problemi che possono verificarsi durante l'esecuzione del comando DBCC SHRINKFILE.
  
### <a name="the-file-does-not-shrink"></a>Il file non viene compattato  
Se l'operazione di compattazione viene eseguita senza errori, ma sembra che le dimensioni del file siano rimaste invariate, verificare che lo spazio disponibile da rimuovere sia sufficiente eseguendo una delle operazioni seguenti:
- Eseguire la query seguente.  
  
```sql
SELECT name ,size/128.0 - CAST(FILEPROPERTY(name, 'SpaceUsed') AS int)/128.0 AS AvailableSpaceInMB
FROM sys.database_files;
```

-   Eseguire il comando [DBCC SQLPERF](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md) per restituire lo spazio usato nel log delle transazioni.  
Se lo spazio disponibile non è sufficiente, l'operazione di compattazione non può ridurre ulteriormente le dimensioni del file.
  
In genere è il file di log a causare problemi di compattazione. Questo è in genere il risultato del mancato troncamento del file di log. È possibile troncare il log impostando il modello di recupero del database con registrazione minima o eseguendo il backup del log e quindi eseguendo nuovamente l'operazione DBCC SHRINKFILE.
  
### <a name="the-shrink-operation-is-blocked"></a>L'operazione di compattazione è bloccata  
È possibile che le operazioni di compattazione vengano bloccate da una transazione che eseguita in un [livello di isolamento basato sul controllo della versione delle righe](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md). Ad esempio, se viene eseguita un'operazione DBCC SHRINK DATABASE mentre è in corso un'operazione di eliminazione di grandi dimensioni che utilizza un livello di isolamento basato sul controllo delle versioni delle righe, l'operazione di compattazione dei file viene rimandata fino al completamento dell'operazione di eliminazione. In questo caso viene registrato un messaggio informativo nel log degli errori di SQL Server (il messaggio 5202 per SHRINKDATABASE e il messaggio 5203 per SHRINKFILE) ogni cinque minuti nella prima ora e quindi ogni ora. Ad esempio, se il log degli errori contiene il messaggio di errore seguente, si verificherà l'errore seguente:
  
```sql
DBCC SHRINKFILE for file ID 1 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
Questo significa che l'operazione di compattazione è bloccata da transazioni snapshot con timestamp precedenti a 109, ovvero all'ultima transazione completata dall'operazione di compattazione. Il messaggio indica inoltre che la colonna **transaction_sequence_num** o **first_snapshot_sequence_num** nella DMV [sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) contiene un valore 15. Se la colonna **transaction_sequence_num** o **first_snapshot_sequence_num** nella visualizzazione contiene un numero minore rispetto all'ultima transazione completata da un'operazione di compattazione (109), l'operazione di compattazione attenderà il completamento delle transazioni.
  
Per risolvere il problema, è possibile eseguire una delle attività seguenti:
-   Terminare la transazione che blocca l'operazione di compattazione.
-   Terminare l'operazione di compattazione. Se l'operazione viene terminata, le operazioni completate fino a quel momento vengono mantenute.  
-   Non eseguire alcuna operazione per consentire che l'operazione di compattazione venga rimandata fino al completamento della transazione di blocco.  
  
## <a name="permissions"></a>Permissions  
È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** o al ruolo predefinito del database **db_owner** .
  
## <a name="examples"></a>Esempi  
  
### <a name="a-shrinking-a-data-file-to-a-specified-target-size"></a>A. Compattazione di un file di dati fino alle dimensioni di destinazione specificate  
Nell'esempio seguente le dimensioni di un file di dati denominato `DataFile1` nel database utente `UserDB` vengono compattate fino a 7 MB.
  
```sql  
USE UserDB;  
GO  
DBCC SHRINKFILE (DataFile1, 7);  
GO  
```  
  
### <a name="b-shrinking-a-log-file-to-a-specified-target-size"></a>B. Compattazione di un file di log fino alle dimensioni di destinazione specificate  
Nell'esempio seguente il file di log nel database `AdventureWorks` viene compattato fino a 1 MB. Per consentire al comando DBCC SHRINKFILE di eseguire la compattazione, il file viene innanzitutto troncato impostando il modello di recupero del database con registrazione minima.
  
```sql  
USE AdventureWorks2012;  
GO  
-- Truncate the log by changing the database recovery model to SIMPLE.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY SIMPLE;  
GO  
-- Shrink the truncated log file to 1 MB.  
DBCC SHRINKFILE (AdventureWorks2012_Log, 1);  
GO  
-- Reset the database recovery model.  
ALTER DATABASE AdventureWorks2012  
SET RECOVERY FULL;  
GO  
```  
  
### <a name="c-truncating-a-data-file"></a>C. Troncamento di un file di dati  
Nell'esempio seguente viene troncato il file di dati primario nel database `AdventureWorks`. Viene eseguita una query sulla vista del catalogo `sys.database_files` per ottenere il `file_id` del file di dati.
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT file_id, name  
FROM sys.database_files;  
GO  
DBCC SHRINKFILE (1, TRUNCATEONLY);  
```  
  
### <a name="d-emptying-a-file"></a>D. Svuotamento di un file  
Nell'esempio seguente viene illustrata la procedura di svuotamento di un file in modo che sia possibile rimuoverlo dal database. Ai fini di questo esempio, viene innanzitutto creato un file di dati e si presuppone che tale file contenga dati.
  
```sql  
USE AdventureWorks2012;  
GO  
-- Create a data file and assume it contains data.  
ALTER DATABASE AdventureWorks2012   
ADD FILE (  
    NAME = Test1data,  
    FILENAME = 'C:\t1data.ndf',  
    SIZE = 5MB  
    );  
GO  
-- Empty the data file.  
DBCC SHRINKFILE (Test1data, EMPTYFILE);  
GO  
-- Remove the data file from the database.  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE Test1data;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)  
[FILE_ID &#40;Transact-SQL&#41;](../../t-sql/functions/file-id-transact-sql.md)  
[sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[Compattare un file](../../relational-databases/databases/shrink-a-file.md)
  
  
