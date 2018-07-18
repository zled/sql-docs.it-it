---
title: DBCC SHRINKDATABASE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DBCC_SHRINKDATABASE_TSQL
- DBCC SHRINKDATABASE
- SHRINKDATABASE_TSQL
- SHRINKDATABASE
dev_langs:
- TSQL
helpviewer_keywords:
- data shrinking [SQL Server]
- shrinking files
- shrinking databases
- DBCC SHRINKDATABASE statement
- decreasing database size
- file shrinking [SQL Server]
- database shrinking [SQL Server]
- logs [SQL Server], shrinking
- reducing database size
ms.assetid: fc976afd-1edb-4341-bf41-c4a42a69772b
caps.latest.revision: 62
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: e6022b5609c2d4b4d362f90088bee4e84ad874c7
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34236412"
---
# <a name="dbcc-shrinkdatabase-transact-sql"></a>DBCC SHRINKDATABASE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Compatta le dimensioni dei file di dati e di log nel database specificato.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC SHRINKDATABASE   
( database_name | database_id | 0   
     [ , target_percent ]   
     [ , { NOTRUNCATE | TRUNCATEONLY } ]   
)  
[ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name* | *database_id* | 0  
 Nome o ID del database che si desidera compattare. Se si specifica 0, viene utilizzato il database corrente.  
  
 *target_percent*  
 Percentuale di spazio che si desidera rendere disponibile nel file del database dopo la compattazione.  
  
 NOTRUNCATE  
 Compatta i dati nei file di dati spostando le pagine allocate dalla fine di un file a pagine non allocate all'inizio del file. *target_percent* è facoltativo. Questa opzione non è supportata con Azure SQL Data Warehouse. 
  
 Lo spazio disponibile alla fine del file non viene restituito al sistema operativo e le dimensioni fisiche del file rimangono invariate. Pertanto, quando si specifica NOTRUNCATE, sembra che il database non venga compattato.  
  
 NOTRUNCATE è applicabile solo ai file di dati. Il file di log non è interessato.  
  
 TRUNCATEONLY  
 Rilascia tutto lo spazio disponibile alla fine del file al sistema operativo senza eseguire alcuno spostamento di pagine all'interno del file. Il file di dati viene compattato solo fino all'ultimo extent allocato. *target_percent* viene ignorato se specificato con TRUNCATEONLY. Questa opzione non è supportata con Azure SQL Data Warehouse.
  
 TRUNCATEONLY interessa il file di log. Per troncare solo il file di dati, utilizzare DBCC SHRINKFILE.  
  
 WITH NO_INFOMSGS  
 Evita la visualizzazione di tutti i messaggi informativi con livello di gravità compreso tra 0 e 10.  
  
## <a name="result-sets"></a>Set di risultati  
Nella tabella seguente vengono descritte le colonne del set di risultati.
  
|Nome colonna|Descrizione|  
|-----------------|-----------------|  
|**DbId**|Numero di identificazione del database del file che [!INCLUDE[ssDE](../../includes/ssde-md.md)] tenta di compattare.|  
|**FileId**|Numero di identificazione del file che [!INCLUDE[ssDE](../../includes/ssde-md.md)] tenta di compattare.|  
|**CurrentSize**|Numero di pagine da 8 KB attualmente occupate dal file.|  
|**MinimumSize**|Numero minimo di pagine da 8 KB che il file può occupare. Corrisponde alle dimensioni minime o alle dimensioni originali di un file.|  
|**UsedPages**|Numero di pagine da 8 KB utilizzate dal file.|  
|**EstimatedPages**|Numero di pagine da 8 KB calcolato da [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Corrisponde alle possibili dimensioni finali del file compattato.|  
  
>[!NOTE]
> [!INCLUDE[ssDE](../../includes/ssde-md.md)] non visualizza alcuna riga per i file non compattati.  
  
## <a name="remarks"></a>Remarks  

>[!NOTE]
> Azure SQL Data Warehouse attualmente non supporta DBCC SHRINKDATABASE. L'esecuzione di questo comando non è consigliata poiché si tratta di un'operazione a elevato utilizzo di input/output che può portare il data warehouse offline. Inoltre, l'esecuzione di questo comando comporta costi per gli snapshot del data warehouse. 

Per compattare tutti i file di dati e di log per un database specifico, eseguire il comando DBCC SHRINKDATABASE. Per compattare un file di dati o di log alla volta per un database specifico, eseguire il comando [DBCC SHRINKFILE](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md).
  
Per visualizzare la quantità corrente di spazio disponibile, ovvero non allocato, nel database, eseguire [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md).
  
È possibile arrestare le istruzioni DBCC SHRINKDATABASE in qualsiasi momento, senza perdere il lavoro completato.
  
Non è possibile ridurre il database a dimensioni inferiori a quelle minime. Le dimensioni minime corrispondono a quelle specificate al momento della creazione del database o alle ultime dimensioni impostate in modo esplicito tramite un'operazione di modifica delle dimensioni dei file, ad esempio DBCC SHRINKFILE o ALTER DATABASE. Ad esempio, se è stato creato un database con dimensioni pari a 10 MB e le dimensioni sono aumentate fino a 100 MB, è possibile compattare il database fino a un minimo di 10 MB, anche se tutti i dati nel database sono stati eliminati.
  
Eseguire DBCC SHRINKDATABASE senza specificare l'opzione NOTRUNCATE o TRUNCATEONLY equivale a eseguire un'operazione DBCC SHRINKDATABASE con NOTRUNCATE seguita da un'operazione DBCC SHRINKDATABASE con TRUNCATEONLY.
  
Il database in fase di compattazione non deve essere necessariamente in modalità utente singolo. Altri utenti possono infatti utilizzare il database durante il processo di compattazione. Questo vale anche per i database di sistema.
  
Non è possibile compattare un database mentre ne viene eseguito il backup e non è possibile eseguire il backup di un database mentre è in corso un'operazione di compattazione.
  
## <a name="how-dbcc-shrinkdatabase-works"></a>Funzionamento di DBCC SHRINKDATABASE  
DBCC SHRINKDATABASE compatta i file di dati uno alla volta mentre i file di log vengono compattati come se fossero inclusi in un pool di log contigui. I file vengono compattati sempre a partire dalla fine.
  
Si consideri un database denominato **mydb** con un file di dati e due file di log. I file di dati e di log hanno una dimensione di 10 MB ciascuno e il file di dati contiene 6 MB di dati.
  
Per ogni file, [!INCLUDE[ssDE](../../includes/ssde-md.md)] calcola le dimensioni di destinazione in base alle quali il file deve essere compattato. Quando DBCC SHRINKDATABASE è specificato con *target_percent*, [!INCLUDE[ssDE](../../includes/ssde-md.md)] calcola la dimensione di destinazione come *target_percent* dello spazio disponibile nel file dopo la compattazione. Ad esempio, se si specifica un valore *target_percent* di 25 per la compattazione di **mydb**, [!INCLUDE[ssDE](../../includes/ssde-md.md)] calcola la dimensione di destinazione del file di dati come 8 MB, ovvero 6 MB di dati e 2 MB di spazio disponibile. Di conseguenza, [!INCLUDE[ssDE](../../includes/ssde-md.md)] sposta i dati degli ultimi 2 MB del file di dati nello spazio disponibile nei primi 8 MB del file di dati e quindi compatta il file.
  
Si supponga che il file di dati di **mydb** contenga 7 MB di dati. Specificando un valore *target_percent* di 30, il file di dati può essere compattato alla percentuale disponibile di 30. Tuttavia, specificando un valore *target_percent* di 40, il file di dati non viene compattato perché [!INCLUDE[ssDE](../../includes/ssde-md.md)] non compatta un file a una dimensione minore di quella occupata attualmente dai dati. Questo concetto può essere descritto anche in modo diverso: il 40% di spazio disponibile desiderato + il 70% del file di dati completo (7 dei 10 MB) è maggiore del 100%. Poiché la percentuale disponibile desiderata più la percentuale corrente occupata dal file di dati supera il 100% (del 10%), qualsiasi valore *target_size* maggiore di 30 non compatterà il file di dati.
  
Per i file di log, [!INCLUDE[ssDE](../../includes/ssde-md.md)] usa *target_percent* per calcolare la dimensione di destinazione dell'intero log; di conseguenza, *target_percent* è la quantità di spazio disponibile nel log dopo l'operazione di compattazione. Le dimensioni di destinazione per l'intero log vengono quindi convertite nelle dimensioni di destinazione per ogni file di log.
  
DBCC SHRINKDATABASE tenta di compattare immediatamente ogni file di log fisico fino alle dimensioni di destinazione specificate. Se i log virtuali non includono alcuna parte del log logico oltre le dimensioni di destinazione del file di log, il file viene troncato correttamente e DBCC SHRINKDATABASE viene completata senza visualizzare alcun messaggio. Se invece i log virtuali includono parti del log logico oltre le dimensioni di destinazione, [!INCLUDE[ssDE](../../includes/ssde-md.md)] libera la maggior quantità di spazio possibile e viene visualizzato un messaggio informativo in cui sono descritte le operazioni necessarie per estrarre le parti del log logico dai log virtuali alla fine del file. Dopo l'esecuzione di queste operazioni, è possibile utilizzare DBCC SHRINKDATABASE per liberare lo spazio rimanente.
  
Poiché è possibile compattare un file di log solo fino al limite del file di log virtuale, potrebbe essere impossibile compattare un file di log fino a ottenere dimensioni inferiori rispetto a quelle del file di log virtuale, anche se non viene utilizzato. Le dimensioni del file di log virtuale vengono scelte in modo dinamico da [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante la creazione o l'estensione dei file di log.
  
## <a name="best-practices"></a>Procedure consigliate  
Quando si pianifica la compattazione di un database, considerare le informazioni seguenti:
-   Un'operazione di compattazione è più efficace dopo l'esecuzione di un'operazione che crea una quantità elevata di spazio inutilizzato, ad esempio il troncamento o l'eliminazione di una tabella.  
-   La maggior parte dei database richiede spazio disponibile per lo svolgimento delle normali attività quotidiane. Se si compatta ripetutamente un database ma le sue dimensioni aumentano di nuovo significa che lo spazio compattato è necessario per le normali operazioni. In questi casi è inutile compattare ripetutamente il database.  
-   L'operazione di compattazione generalmente aumenta la frammentazione degli indici del database. Questo è un ulteriore motivo per evitare di compattare ripetutamente un database.  
-   Se non è necessario soddisfare esigenze specifiche, non impostare l'opzione di database AUTO_SHRINK su ON.  
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
 È possibile che le operazioni di compattazione vengano bloccate da una transazione che eseguita in un [livello di isolamento basato sul controllo della versione delle righe](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md). Ad esempio, se viene eseguita un'operazione DBCC SHRINK DATABASE mentre è in corso un'operazione di eliminazione di grandi dimensioni che utilizza un livello di isolamento basato sul controllo delle versioni delle righe, l'operazione di compattazione dei file viene rimandata fino al completamento dell'operazione di eliminazione. In questo caso viene registrato un messaggio informativo nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (il messaggio 5202 per SHRINKDATABASE e il messaggio 5203 per SHRINKFILE) ogni cinque minuti nella prima ora e quindi ogni ora. Ad esempio, il log degli errori può contenere il messaggio di errore seguente:  
  
```sql
DBCC SHRINKDATABASE for database ID 9 is waiting for the snapshot   
transaction with timestamp 15 and other snapshot transactions linked to   
timestamp 15 or with timestamps older than 109 to finish.  
```  
  
Questo significa che l'operazione di compattazione è bloccata da transazioni snapshot con timestamp precedenti a 109, ovvero all'ultima transazione completata dall'operazione di compattazione. Il messaggio indica anche che la colonna **transaction_sequence_num** o **first_snapshot_sequence_num** nella DMV [sys.dm_tran_active_snapshot_database_transactions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md) contiene un valore 15. Se la colonna **transaction_sequence_num** o **first_snapshot_sequence_num** nella visualizzazione contiene un numero minore rispetto all'ultima transazione completata da un'operazione di compattazione (109), l'operazione di compattazione attenderà il completamento delle transazioni.
  
Per risolvere il problema, è possibile eseguire una delle attività seguenti:
-   Terminare la transazione che blocca l'operazione di compattazione.  
-   Terminare l'operazione di compattazione. Il lavoro completato fino a quel momento viene mantenuto.  
-   Non eseguire alcuna operazione per consentire che l'operazione di compattazione venga rimandata fino al completamento della transazione di blocco.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** o al ruolo predefinito del database **db_owner** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-shrinking-a-database-and-specifying-a-percentage-of-free-space"></a>A. Compattazione di un database e impostazione di una percentuale di spazio disponibile  
 Nell'esempio seguente vengono ridotte le dimensioni dei file di dati e di log nel database utente `UserDB` per ottenere il 10% di spazio disponibile nel database.  
  
```sql  
DBCC SHRINKDATABASE (UserDB, 10);  
GO  
```  
  
### <a name="b-truncating-a-database"></a>B. Troncamento di un database  
 Nell'esempio seguente i file di dati e di log nel database di esempio `AdventureWorks` vengono compattati fino all'ultimo extent allocato.  
  
```sql  
DBCC SHRINKDATABASE (AdventureWorks2012, TRUNCATEONLY);  
```  
  
## <a name="see-also"></a>Vedere anche  
[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)  
[Compattare un database](../../relational-databases/databases/shrink-a-database.md)
  
  
