---
title: "Caricamento dati di indici columnstore | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b29850b5-5530-498d-8298-c4d4a741cdaf
caps.latest.revision: 31
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 28
---
# Caricamento dati di indici columnstore
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Caricare dati in un indice columnstore usando i metodi standard di caricamento bulk di SQL e di inserimento singolo. Tali metodi includono bcp, Integration Services e l'istruzione merge o insert di Transact-SQL.  
  
 Se non si ha esperienza con gli indici columnstore, vedere i termini e i concetti illustrati in [Guida agli indici columnstore](../Topic/Columnstore%20Indexes%20Guide.md).  
  
 Sono necessarie informazioni più dettagliate? Vedere questo [post di blog](http://blogs.msdn.com/b/sqlcat/archive/2015/03/11/data-loading-performance-considerations-on-tables-with-clustered-columnstore-index.aspx).  
  
##  <a name="dataload_cci"></a> Caricamento bulk in un indice columnstore cluster  
 Per eseguire il caricamento bulk di righe in un indice columnstore cluster, è possibile usare lo strumento da riga di comando bcp, Integration Services, oppure selezionare le righe da una tabella di gestione temporanea.  
  
 ![Caricamento in un indice cluster columnstore](../../relational-databases/indexes/media/sql-server-pdw-columnstore-loadprocess.gif "Caricamento in un indice cluster columnstore")  
  
 Come illustrato nel diagramma, un caricamento bulk:  
  
1.  Non esegue il preordinamento dei dati. I dati vengono inseriti nei rowgroup secondo l'ordine di ricezione.  
  
2.  Se le dimensioni del batch sono > = 102.400, le righe vengono caricate direttamente nei rowgroup compressi. Affinché l'importazione bulk sia efficiente è consigliabile scegliere una dimensione di batch > = 102.400, poiché è possibile evitare lo spostamento di righe di dati in un rowgroup delta prima che le righe siano spostate nei rowgroup compressi da un thread in background, dal motore di tuple.  
  
3.  Se le dimensioni del batch sono < 102.400 o se le righe rimanenti sono < 102.400, le righe vengono caricate in rowgroup delta.  
  
 Per il caricamento bulk in indici columnstore cluster sono disponibili le ottimizzazioni seguenti.  
  
-   Caricamento parallelo: è possibile eseguire importazioni in blocco simultanee (bcp o bulk insert) importando ogni caricamento in un file di dati separato. A differenza di rowstore, non è necessario specificare TABLOCK, poiché ogni thread di importazione in blocco caricherà i dati esclusivamente in un rowgroup distinto (compresso o delta) che presenta un blocco esclusivo.   Specificando TABLOCK verrà forzato il blocco esclusivo sulla tabella e non sarà possibile importare dati in parallelo.  
  
-   Ottimizzazione dei log: si ha un caricamento bulk con registrazione minima quando i dati vengono caricati in rowgroup compressi. Non si ha registrazione minima quando i dati vengono caricati in rowgroup delta con dimensione del batch < 102.400.  
  
-   Ottimizzazione del blocco: durante il caricamento in rowgroup compressi, viene acquisito il blocco X del rowgroup. Tuttavia, durante il caricamento bulk in rowgroup delta, viene acquisito il blocco X del rowgroup, ma SQL Server continua a bloccare i blocchi di PAGE/EXTENT perché il blocco X del rowgroup non rientra nella gerarchia di blocco.  
  
 In caso di più indici non cluster, non si ha blocco o ottimizzazione della registrazione dell'indice, ma le ottimizzazioni sull'indice columnstore cluster descritte in precedenza sono ancora presenti.  
  
## Funzionamento di deltastore  
 Gli indici columnstore cluster acquisiscono fino a 1.048.576 righe nel deltastore prima di comprimerle nel rowgroup compresso, migliorando così la compressione dell'indice columnstore. Quando un rowgroup deltastore contiene 1.048.576 righe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contrassegna il rowgroup come chiuso. Un processo in background, denominato *motore di tuple*, trova ogni rowgroup chiuso e lo comprime nel columnstore.  
  
 Per ogni indice columnstore cluster possono essere presenti più deltastore.  
  
-   Se un deltastore è bloccato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , si tenterà di ottenere un blocco su un deltastore diverso. Se non esistono deltastore disponibili in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , verrà creato un nuovo deltastore.  
  
-   In una tabella partizionata possono essere presenti più deltastore per ogni partizione.  
  
 Gli scenari seguenti indicano quando le righe caricate vengono direttamente indirizzate al columnstore o passano per il deltastore.  
  
 Nell'esempio, ogni rowgroup può avere 102.400-1.048.576 righe per rowgroup. In pratica, la dimensione massima di un rowgroup può essere inferiore a 1.048.576 righe quando sono presenti richieste di memoria.  
  
|Righe per il caricamento bulk|Righe aggiunte al rowgroup compresso|Righe aggiunte al rowgroup delta|  
|-----------------------|-------------------------------------------|--------------------------------------|  
|102.000|0|102.000|  
|145.000|145.000<br /><br /> Dimensioni rowgroup: 145.000.|0|  
|1.048.577|1,048,576<br /><br /> Dimensioni rowgroup: 1.048.576.|1|  
|2.252.152|2.252.152<br /><br /> Dimensioni rowgroup: 1.048.576, 1.048.576, 155.000.|0|  
  
 Nell'esempio seguente vengono illustrati i risultati del caricamento di 1.048.577 righe in una tabella. I risultati mostrano che esiste un rowgroup COMPRESSED nel columnstore (come segmenti di colonna compressi) e 1 riga nel deltastore.  
  
```  
SELECT object_id, index_id, partition_number, row_group_id, delta_store_hobt_id, state state_desc, total_rows, deleted_rows, size_in_bytes   
FROM sys.dm_db_column_store_row_group_physical_stats  
```  
  
 ![Rowgroup and deltastore for a batch load](../../relational-databases/indexes/media/sql-server-pdw-columnstore-batchload.gif "Rowgroup and deltastore for a batch load")  
  
## Caricamento da una tabella di gestione temporanea  
 Il modello comune per il caricamento di dati consiste nel caricare i dati in una tabella di gestione temporanea, eseguire alcune trasformazioni e quindi caricare i dati nella tabella di destinazione usando il comando seguente  
  
```  
INSERT INTO <columnstore index>  SELECT <list of columns> FROM <Staging Table>  
  
```  
  
 Il comando carica i dati nell'indice columnstore in modo analogo ai comandi bcp o bulk insert, ma in un unico batch. Se il numero di righe nella tabella di gestione temporanea è < 102.400, le righe vengono caricate in un rowgroup delta, altrimenti possono essere caricate direttamente in un rowgroup compresso.  Uno dei limiti principali è dato dal fatto che l'operazione INSERT è a thread singolo. Per caricare i dati in parallelo, è possibile creare più tabelle di gestione temporanea o immettere i comandi INSERT/SELECT con intervalli non sovrapposti di righe dalla tabella di gestione temporanea.  Questa limitazione è stata risolta in SQL Server 2016. Il comando seguente carica i dati dalla tabella di gestione temporanea in parallelo, ma è necessario specificare il comando TABLOCK.  
  
```  
INSERT INTO <columnstore index>  WITH (TABLOCK)  SELECT <list of columns> FROM <Staging Table>  
```  
  
 Per il caricamento in indici columnstore cluster da una tabella di gestione temporanea sono disponibili le ottimizzazioni seguenti.  
  
-   Ottimizzazione dei log: con registrazione minima quando i dati vengono caricati in rowgroup compressi. Non si ha registrazione minima quando i dati vengono caricati in rowgroup delta.  
  
-   Ottimizzazione del blocco: durante il caricamento in rowgroup compressi, viene acquisito il blocco X del rowgroup. Tuttavia, quando si opera con rowgroup delta viene acquisito il blocco X del rowgroup, ma SQL Server continua a bloccare i blocchi di PAGE/EXTENT perché il blocco X del rowgroup non rientra nella gerarchia di blocco.  
  
 In caso di più indici non cluster, non si ha blocco o ottimizzazione della registrazione dell'indice, ma le ottimizzazioni sull'indice columnstore cluster descritte in precedenza sono ancora presenti.  
  
## Caricamento con inserimento singolo  
 L'*inserimento singolo* indica il modo in cui le righe vengono caricate nel columnstore mediante l'istruzione INSERT INTO. Ogni riga viene aggiunta a un rowgroup delta. Le singole righe passano direttamente nel rowgroup deltastore, dove si accumulano fino alla chiusura del rowgroup, ovvero al raggiungimento di 1.048.576 righe o finché l'indice columnstore non viene ricompilato.  
  
```  
INSERT INTO <table-name> VALUES (<set of values>)  
```  
  
 Si noti che i thread simultanei che usano INSERT INTO per inserire valori in un indice columnstore cluster possono inserire righe nello stesso rowgroup deltastore.  
  
 Quando il rowgroup arriva a contenere 1.048.576 righe viene contrassegnato come chiuso, ma è ancora disponibile per query e operazioni di aggiornamento/eliminazione. Le righe appena inserite verranno indirizzate in un rowgroup deltastore già esistente o nuovo. In background agisce il *motore di tuple*, che comprime i rowgroup delta chiusi ogni 5 minuti circa. È possibile richiamare in modo esplicito il comando seguente per comprimere il rowgroup delta chiuso:  
  
```  
ALTER INDEX <index-name> on <table-name> REORGANIZE  
```  
  
 Per forzare un rowgroup delta chiuso e compresso, eseguire il comando seguente. È consigliabile eseguire questo comando al termine del caricamento delle righe, quando non si prevede l'aggiunta di nuove righe. La chiusura e la compressione esplicita del rowgroup delta consente di risparmiare spazio di archiviazione e incrementare le prestazioni delle query di analisi. È consigliabile richiamare questo comando quando non si prevede l'inserimento di nuove righe.  
  
```  
ALTER INDEX <index-name> on <table-name> REORGANIZE with (COMPRESS_ALL_ROW_GROUPS = ON)  
```  
  
## Caricamento in una tabella partizionata  
 Per i dati partizionati, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assegna prima ogni riga a una partizione, quindi esegue operazioni columnstore sui dati nella partizione. Ogni partizione ha i propri rowgroup e almeno un deltastore.  
  
## Caricamento in un indice columnstore non cluster  
 In una tabella rowstore con dati di un indice columnstore non cluster, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inserisce sempre i dati nella tabella di base. I dati non vengono mai inseriti direttamente nell'indice columnstore.  
  
## Vedere anche  
 [Guida agli indici columnstore](../Topic/Columnstore%20Indexes%20Guide.md)   
 [Riepilogo delle funzionalità con versione degli indici columnstore](../Topic/Columnstore%20Indexes%20Versioned%20Feature%20Summary.md)   
 [Prestazioni delle query per gli indici columnstore](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [Introduzione a columnstore per l'analisi operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [Indici columnstore per il data warehousing](../Topic/Columnstore%20Indexes%20for%20Data%20Warehousing.md)   
 [Deframmentazione degli indici columnstore](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
  