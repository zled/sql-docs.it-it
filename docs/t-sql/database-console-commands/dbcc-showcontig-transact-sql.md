---
title: L'istruzione DBCC SHOWCONTIG (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC_SHOWCONTIG_TSQL
- DBCC SHOWCONTIG
- SHOWCONTIG
- SHOWCONTIG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- displaying defragmentation information
- DBCC SHOWCONTIG statement
- defragmenting indexes
- leaf level defragmenting
- fragmentation [SQL Server]
- index defragmenting [SQL Server]
ms.assetid: 1df2123a-1197-4fff-91a3-25e3d8848aaa
caps.latest.revision: 78
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 770b21498e0159c1ac30eb4ea8a192b6597b4ebe
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-showcontig-transact-sql"></a>DBCC SHOWCONTIG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Visualizza informazioni sulla frammentazione dei dati e degli indici per la tabella o vista specificata.
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilizzare [Sys.dm db_index_physical_stats](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) invece.  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [versione](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC SHOWCONTIG   
[ (   
    { table_name | table_id | view_name | view_id }   
    [ , index_name | index_id ]   
) ]   
    [ WITH   
        {   
         [ , [ ALL_INDEXES ] ]   
         [ , [ TABLERESULTS ] ]   
         [ , [ FAST ] ]  
         [ , [ ALL_LEVELS ] ]   
         [ NO_INFOMSGS ]  
         }  
    ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *TABLE_NAME* | *table_id* | *view_name* | *view_id*  
 Tabella o vista di cui controllare le informazioni sulla frammentazione. Se viene omesso, vengono controllate tutte le tabelle e le viste indicizzate nel database corrente. Per ottenere la tabella o visualizzare l'ID, utilizzare il [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md) (funzione).  
  
 *index_name* | *index_id*  
 Indice di cui controllare le informazioni sulla frammentazione. Se viene omesso, l'istruzione elabora l'indice di base per la tabella o vista specificata. Per ottenere l'ID di indice, utilizzare il [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo.  
  
 con  
 Specifica le opzioni per il tipo di informazioni restituite dall'istruzione DBCC.  
  
 FAST  
 Specifica se eseguire un'analisi rapida dell'indice con restituzione di informazioni di output minime. Durante un'analisi rapida non vengono lette le pagine del livello foglia o dati dell'indice.  
  
 ALL_INDEXES  
 Visualizza i risultati per tutti gli indici delle tabelle e viste specificate, anche se viene indicato un indice specifico.  
  
 TABLERESULTS  
 Visualizza i risultati come set di righe, con informazioni aggiuntive.  
  
 ALL_LEVELS  
 Supportata per compatibilità con le versioni precedenti. Anche se si specifica ALL_LEVELS, viene elaborato solo il livello foglia dell'indice oppure il livello dati della tabella.  
  
 NO_INFOMSGS  
 Evita la visualizzazione di tutti i messaggi informativi con livello di gravità compreso tra 0 e 10.  
  
## <a name="result-sets"></a>Set di risultati  
Nella tabella seguente vengono descritte le informazioni del set di risultati.
  
|Statistiche|Description|  
|---|---|
|**Pagine sottoposte ad analizzate**|Numero di pagine della tabella o dell'indice.|  
|**Extent sottoposti ad analizzate**|Numero di extent della tabella o dell'indice.|  
|**Cambi di extent**|Numero di passaggi dell'istruzione DBCC da un extent all'altro durante l'attraversamento delle pagine della tabella o dell'indice.|  
|**Byte Pagine per Extent**|Numero di pagine per extent nella catena di pagine.|  
|**Densità di analisi [conteggio ottimale: conteggio effettivo]**|Valore percentuale. Rapporto tra **conteggio ottimale** a **conteggio effettivo**. Questo valore è 100 se tutti gli elementi sono contigui, è minore di 100 in presenza di frammentazioni.<br /><br /> **Conteggio ottimale** rappresenta il numero ideale di cambi di extent se tutti gli elementi fossero contigui. **Conteggio effettivo** è il numero effettivo di cambi di extent.|  
|**Frammentazione analisi logica**|Percentuale di pagine non ordinate restituite dall'analisi delle pagine foglia di un indice. Questo valore non è rilevante per gli heap. Una pagina in ordine è una pagina per cui la pagina fisica successiva allocata all'indice non è la pagina a cui fa riferimento il quando*e* puntatore nella pagina foglia corrente.|  
|**Frammentazione analisi extent**|Percentuale di extent non ordinati rilevati durante l'analisi delle pagine foglia di un indice. Questo valore non è rilevante per gli heap. Un extent risulta non ordinato quando l'extent contenente la pagina corrente di un indice non corrisponde fisicamente all'extent successivo a quello che contiene la pagina precedente di un indice.<br /><br /> Nota: Questo numero è privo di significato quando l'indice si estende su più file.|  
|**Byte Byte liberi per pagina**|Numero medio di byte disponibili nelle pagine sottoposte ad analisi. Maggiore è il numero, minore sarà il livello di riempimento delle pagine. I numeri minori indicano una situazione migliore se nell'indice non verranno eseguiti numerosi inserimenti casuali. Anche le dimensioni delle righe influiscono su questo valore, che risulta maggiore per righe di grandi dimensioni.|  
|**Byte Densità pagina (completa)**|Densità media della pagina, in percentuale. Questo valore tiene conto delle dimensioni delle righe e pertanto rappresenta un'indicazione più precisa dell'effettivo livello di riempimento delle pagine. Sono preferibili valori elevati.|  
  
Quando *table_id* e FAST vengono specificati, DBCC SHOWCONTIG restituisce un set di risultati con solo le colonne seguenti.
-   **Pagine sottoposte ad analizzate**  
-   **Cambi di extent**  
-   **Densità di analisi [conteggio ottimale: conteggio effettivo]**  
-   **Frammentazione analisi extent**  
-   **Frammentazione analisi logica**  
  
Se si specifica TABLERESULTS, DBCC SHOWCONTIG restituisce le colonne seguenti oltre alle nove colonne descritte nella tabella precedente.
  
|Statistiche|Description|  
|---|---|
|**nome oggetto**|Nome della tabella o vista elaborata.|  
|**ObjectId**|ID del nome di oggetto.|  
|**IndexName**|Nome dell'indice elaborato. NULL per un heap.|  
|**IndexId**|ID dell'indice. 0 per un heap.|  
|**Level**|Livello dell'indice. Il livello 0 corrisponde al livello foglia (o dati) dell'indice.<br /><br /> Il livello è 0 per un heap.|  
|**Pagine**|Numero di pagine che compongono tale livello dell'indice o l'intero heap.|  
|**Righe**|Numero di record di dati o dell'indice a tale livello dell'indice. Nel caso di un heap, corrisponde al numero di record di dati dell'intero heap.<br /><br /> Per un heap, il numero di record restituito da questa funzione potrebbe non corrispondere al numero di righe restituito eseguendo un SELECT COUNT (*) sull'heap. Questo perché una riga potrebbe contenere più record. Ad esempio, in alcune situazioni di aggiornamento, un'unica riga dell'heap potrebbe presentare un record di inoltro e un record inoltrato a seguito dell'operazione di aggiornamento. Inoltre, nell'archiviazione LOB_DATA la maggior parte delle righe LOB viene suddivisa in più record.|  
|**MinimumRecordSize**|Dimensioni minime dei record in tale livello dell'indice o nell'intero heap.|  
|**MaximumRecordSize**|Dimensioni massime dei record in tale livello dell'indice o nell'intero heap.|  
|**AverageRecordSize**|Dimensioni medie dei record in tale livello dell'indice o nell'intero heap.|  
|**ForwardedRecords**|Numero di record inoltrati in tale livello dell'indice o nell'intero heap.|  
|**Extent**|Numero di extent in tale livello dell'indice o nell'intero heap.|  
|**ExtentSwitches**|Numero di passaggi dell'istruzione DBCC da un extent all'altro durante l'attraversamento delle pagine della tabella o dell'indice.|  
|**AverageFreeBytes**|Numero medio di byte disponibili nelle pagine sottoposte ad analisi. Maggiore è il numero, minore sarà il livello di riempimento delle pagine. I numeri minori indicano una situazione migliore se nell'indice non verranno eseguiti numerosi inserimenti casuali. Anche le dimensioni delle righe influiscono su questo valore, che risulta maggiore per righe di grandi dimensioni.|  
|**AveragePageDensity**|Densità media della pagina, in percentuale. Questo valore tiene conto delle dimensioni delle righe e pertanto rappresenta un'indicazione più precisa dell'effettivo livello di riempimento delle pagine. Sono preferibili valori elevati.|  
|**ScanDensity**|Valore percentuale. Rapporto tra **BestCount** a **ActualCount**. Questo valore è 100 se tutti gli elementi sono contigui, è minore di 100 in presenza di frammentazioni.|  
|**BestCount**|Rappresenta il numero ideale di cambi di extent se tutti gli elementi fossero contigui.|  
|**ActualCount**|Rappresenta il numero effettivo di cambi di extent.|  
|**LogicalFragmentation**|Percentuale di pagine non ordinate restituite dall'analisi delle pagine foglia di un indice. Questo valore non è rilevante per gli heap. Una pagina in ordine è una pagina per cui la pagina fisica successiva allocata all'indice non è la pagina a cui fa riferimento il quando*e* puntatore nella pagina foglia corrente.|  
|**ExtentFragmentation**|Percentuale di extent non ordinati rilevati durante l'analisi delle pagine foglia di un indice. Questo valore non è rilevante per gli heap. Un extent risulta non ordinato quando l'extent contenente la pagina corrente di un indice non corrisponde fisicamente all'extent successivo a quello che contiene la pagina precedente di un indice.<br /><br /> Nota: Questo numero è privo di significato quando l'indice si estende su più file.|  
  
Se si specificano le opzioni WITH TABLERESULTS e FAST, il set di risultati è uguale a quello restituito specificando WITH TABLERESULTS, con l'eccezione delle colonne seguenti che avranno valori Null:

| Righe| Extents |
|---|---|
|**MinimumRecordSize**|**AverageFreeBytes**|  
|**MaximumRecordSize**|**AveragePageDensity**|  
|**AverageRecordSize**|**ExtentFragmentation**|  
|**ForwardedRecords**||  
  
## <a name="remarks"></a>Osservazioni  
L'istruzione DBCC SHOWCONTIG attraversa la catena di pagine al livello foglia dell'oggetto specificato indice quando *index_id* specificato. Se solo *table_id* è specificato o se *index_id* è 0, le pagine di dati della tabella specificata vengono analizzate. L'operazione richiede esclusivamente un blocco a livello di tabella preventivo condiviso (IS). In questo modo è possibile eseguire tutti gli aggiornamenti e gli inserimenti, con l'eccezione delle operazioni che richiedono un blocco a livello di tabella esclusivo (X). Ciò consente di ottenere una velocità di esecuzione accettabile senza riduzione della concorrenza per il numero di statistiche restituite. Tuttavia, se il comando viene utilizzato esclusivamente per ottenere dati di misurazione della frammentazione, è consigliabile utilizzare l'opzione WITH FAST per ottenere prestazioni ottimali. Durante un'analisi rapida non vengono lette le pagine del livello foglia o dati dell'indice. L'opzione WITH FAST non si applica a un heap.
  
## <a name="restrictions"></a>Restrizioni  
DBCC SHOWCONTIG non visualizza dati con **ntext**, **testo**, e **immagine** tipi di dati. La mancata visualizzazione è dovuta al fatto gli indici di testo che archiviano dati di tipo text e image non esistono più.
  
Inoltre, DBCC SHOWCONTIG non supporta alcune nuove caratteristiche. Esempio:
-   Se la tabella o l'indice specificato è partizionato, DBCC SHOWCONTIG visualizza solo la prima partizione della tabella o dell'indice specificato.  
-   DBCC SHOWCONTIG non visualizza informazioni sull'archiviazione di overflow della riga e altri nuovi tipi di dati all'esterno di righe, ad esempio **nvarchar (max)**, **varchar (max)**, **varbinary (max)**, e **xml**.  
-   Gli indici spaziali non sono supportati da DBCC SHOWCONTIG.  
  
Tutte le nuove funzionalità sono completamente supportate dal [Sys.dm db_index_physical_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) vista a gestione dinamica.
  
## <a name="table-fragmentation"></a>Frammentazione della tabella  
L'istruzione DBCC SHOWCONTIG determina se la tabella è molto frammentata. La frammentazione si verifica in seguito ai processi di modifica dei dati della tabella (istruzioni INSERT, UPDATE e DELETE). Poiché tali modifiche in genere non sono distribuite in modo equo tra le righe della tabella, il livello di riempimento di ogni pagina può variare nel corso del tempo. Nel caso di query che eseguono l'analisi di un'intera tabella o di una parte di tabella, tale frammentazione della tabella potrebbe comportare letture di pagine aggiuntive, operazione che ostacola l'analisi parallela dei dati.
  
Per ridurre il livello di frammentazione di un indice molto frammentato, è possibile eseguire una delle operazioni seguenti:
-   Eliminare e ricreare un indice cluster.  
     Quando si ricrea un indice cluster, i dati vengono riorganizzati e si ottengono pagine di dati complete. È possibile configurare il livello di riempimento tramite l'opzione FILLFACTOR dell'istruzione CREATE INDEX. Questo metodo presenta due svantaggi, ovvero l'indice rimane offline durante l'operazione di eliminazione o ricostruzione e l'operazione è atomica. Se la creazione dell'indice viene interrotta, l'indice non viene ricreato.  
-   Ridisporre in ordine logico le pagine del livello foglia dell'indice.  
     Per ridisporre in ordine logico le pagine del livello foglia dell'indice, utilizzare ALTER INDEX…REORGANIZE. L'operazione viene eseguita online e pertanto l'indice rimane disponibile durante l'esecuzione dell'istruzione. È inoltre possibile interrompere l'operazione senza perdere il lavoro completato. Con questo metodo, tuttavia, i dati non vengono riorganizzati in modo altrettanto efficiente di quanto consentito dall'operazione di eliminazione o ricostruzione di un indice cluster.  
-   Ricompilare l'indice.  
     Per ricompilare l'indice, utilizzare ALTER INDEX con REBUILD. Per altre informazioni, vedere [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
Il **Media Byte disponibili per pagina** e **Media Densità pagina (completa)** nel set di risultati indicano il livello di riempimento delle pagine di indice. Il **Media Byte disponibili per pagina** numero deve essere basso e **Media Densità pagina (completa)** deve essere elevato per un indice che non avrà molti inserimenti casuali. L'eliminazione e la ricostruzione di un indice con l'opzione FILLFACTOR può consentire di migliorare tali statistiche. L'istruzione ALTER INDEX con l'opzione REORGANIZE consente inoltre di compattare un indice tenendo conto del valore FILLFACTOR corrispondente, con un conseguente miglioramento delle statistiche.
  
> [!NOTE]  
>  Per un indice con numerosi inserimenti casuali e pagine molto piene si verificherà un maggior numero di divisioni di pagina e di conseguenza una maggiore frammentazione.  
  
È possibile determinare il livello di frammentazione di un indice nei modi seguenti:
-   Confrontando i valori di **cambi di Extent** e **extent sottoposti ad analisi**.  
     Il valore di **cambi di Extent** deve essere il più vicino possibile a quello di **extent sottoposti ad analisi**. Questo rapporto viene calcolato come il **densità di analisi** valore. Tale valore deve essere il più alto possibile e può essere migliorato riducendo la frammentazione dell'indice.  
  
    > [!NOTE]  
    >  Questo metodo non funziona se l'indice è esteso a più file.  
  
-   Grazie alla conoscenza **frammentazione analisi logica** e **frammentazione analisi Extent** valori.  
     **Frammentazione analisi logica** e, in misura minore, **frammentazione analisi Extent** i valori sono i migliori indicatori del livello di frammentazione di una tabella. Entrambi i valori dovrebbero essere il più possibile prossimi allo zero, anche se possono essere accettabili valori compresi tra 0% e 10%.  
  
    > [!NOTE]  
    >  Il **frammentazione analisi Extent** valore sarà elevato se l'indice si estende su più file. Per ridurre questo valore, è necessario ridurre la frammentazione dell'indice.  
  
## <a name="permissions"></a>Permissions  
L'utente deve proprietario della tabella oppure essere un membro del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database, o **db_ddladmin** ruolo predefinito del database.
  
## <a name="examples"></a>Esempi  
### <a name="a-displaying-fragmentation-information-for-a-table"></a>A. Visualizzazione delle informazioni sulla frammentazione di una tabella  
Nell'esempio seguente vengono visualizzate informazioni sulla frammentazione della tabella `Employee`.
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC SHOWCONTIG ('HumanResources.Employee');  
GO  
```  
  
### <a name="b-using-objectid-to-obtain-the-table-id-and-sysindexes-to-obtain-the-index-id"></a>B. Utilizzo di OBJECT_ID per ottenere l'ID della tabella e di sys.indexes per ottenere l'ID dell'indice  
L'esempio seguente usa `OBJECT`_`ID` e `sys.indexes` catalogo per ottenere l'ID di tabella e l'ID di indice per il `AK_Product_Name` indice del `Production.Product` tabella il [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @id int, @indid int  
SET @id = OBJECT_ID('Production.Product')  
SELECT @indid = index_id   
FROM sys.indexes  
WHERE object_id = @id   
   AND name = 'AK_Product_Name'  
DBCC SHOWCONTIG (@id, @indid);  
GO  
```  
  
### <a name="c-displaying-an-abbreviated-result-set-for-a-table"></a>C. Visualizzazione di un set di risultati abbreviato per una tabella  
L'esempio seguente restituisce un risultato abbreviato impostato per il `Product` tabella il [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC SHOWCONTIG ('Production.Product', 1) WITH FAST;  
GO  
```  
  
### <a name="d-displaying-the-full-result-set-for-every-index-on-every-table-in-a-database"></a>D. Visualizzazione del set di risultati completo per ogni indice di tutte le tabelle di un database  
Nell'esempio seguente viene restituito un set completo di risultati relativi a ogni indice di tutte le tabelle del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC SHOWCONTIG WITH TABLERESULTS, ALL_INDEXES;  
GO  
```  
  
### <a name="e-using-dbcc-showcontig-and-dbcc-indexdefrag-to-defragment-the-indexes-in-a-database"></a>E. Utilizzo di DBCC SHOWCONTIG e DBCC INDEXDEFRAG per deframmentare gli indici di un database  
Nell'esempio seguente viene illustrato un metodo semplice per deframmentare tutti gli indici di un database il cui livello di frammentazione è superiore alla soglia massima specificata.
  
```sql
/*Perform a 'USE <database name>' to select the database in which to run the script.*/  
-- Declare variables  
SET NOCOUNT ON;  
DECLARE @tablename varchar(255);  
DECLARE @execstr   varchar(400);  
DECLARE @objectid  int;  
DECLARE @indexid   int;  
DECLARE @frag      decimal;  
DECLARE @maxfrag   decimal;  
  
-- Decide on the maximum fragmentation to allow for.  
SELECT @maxfrag = 30.0;  
  
-- Declare a cursor.  
DECLARE tables CURSOR FOR  
   SELECT TABLE_SCHEMA + '.' + TABLE_NAME  
   FROM INFORMATION_SCHEMA.TABLES  
   WHERE TABLE_TYPE = 'BASE TABLE';  
  
-- Create the table.  
CREATE TABLE #fraglist (  
   ObjectName char(255),  
   ObjectId int,  
   IndexName char(255),  
   IndexId int,  
   Lvl int,  
   CountPages int,  
   CountRows int,  
   MinRecSize int,  
   MaxRecSize int,  
   AvgRecSize int,  
   ForRecCount int,  
   Extents int,  
   ExtentSwitches int,  
   AvgFreeBytes int,  
   AvgPageDensity int,  
   ScanDensity decimal,  
   BestCount int,  
   ActualCount int,  
   LogicalFrag decimal,  
   ExtentFrag decimal);  
  
-- Open the cursor.  
OPEN tables;  
  
-- Loop through all the tables in the database.  
FETCH NEXT  
   FROM tables  
   INTO @tablename;  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
-- Do the showcontig of all indexes of the table  
   INSERT INTO #fraglist   
   EXEC ('DBCC SHOWCONTIG (''' + @tablename + ''')   
      WITH FAST, TABLERESULTS, ALL_INDEXES, NO_INFOMSGS');  
   FETCH NEXT  
      FROM tables  
      INTO @tablename;  
END;  
  
-- Close and deallocate the cursor.  
CLOSE tables;  
DEALLOCATE tables;  
  
-- Declare the cursor for the list of indexes to be defragged.  
DECLARE indexes CURSOR FOR  
   SELECT ObjectName, ObjectId, IndexId, LogicalFrag  
   FROM #fraglist  
   WHERE LogicalFrag >= @maxfrag  
      AND INDEXPROPERTY (ObjectId, IndexName, 'IndexDepth') > 0;  
  
-- Open the cursor.  
OPEN indexes;  
  
-- Loop through the indexes.  
FETCH NEXT  
   FROM indexes  
   INTO @tablename, @objectid, @indexid, @frag;  
  
WHILE @@FETCH_STATUS = 0  
BEGIN  
   PRINT 'Executing DBCC INDEXDEFRAG (0, ' + RTRIM(@tablename) + ',  
      ' + RTRIM(@indexid) + ') - fragmentation currently '  
       + RTRIM(CONVERT(varchar(15),@frag)) + '%';  
   SELECT @execstr = 'DBCC INDEXDEFRAG (0, ' + RTRIM(@objectid) + ',  
       ' + RTRIM(@indexid) + ')';  
   EXEC (@execstr);  
  
   FETCH NEXT  
      FROM indexes  
      INTO @tablename, @objectid, @indexid, @frag;  
END;  
  
-- Close and deallocate the cursor.  
CLOSE indexes;  
DEALLOCATE indexes;  
  
-- Delete the temporary table.  
DROP TABLE #fraglist;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)  
[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[OBJECT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/object-id-transact-sql.md)  
[sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)
  
  


