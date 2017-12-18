---
title: 'Articolo aggiornato: documentazione dei database relazionali | Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato relativi alle modifiche recenti alla documentazione dei database relazionali.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: BYHAM
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.workload: relational-databases
ms.tgt_pltfrm: na
ms.devlang: na
ms.date: 12/02/2017
ms.author: genemi
ms.openlocfilehash: 1fbc7affa833eb34b6e13e28b229d47ac0b05a5c
ms.sourcegitcommit: 29265ad41fbe3326c21c6908ec4275a3a38f1c09
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2017
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Articoli nuovi e aggiornati di recente: documentazione dei database relazionali



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **28/09/2017** &nbsp; - &nbsp; **02/12/2017**
- *Area di interesse:* &nbsp; **database relazionali**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Usare il profiler XEvent di SQL Server Management Studio](extended-events/use-the-ssms-xe-profiler.md)
2. [Procedura guidata per l'importazione di file flat in SQL](import-export/import-flat-file-wizard.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Database tempdb](#TitleNum_1)
2. [Guida sull'architettura di gestione della memoria](#TitleNum_2)
3. [Statistiche](#TitleNum_3)
4. [sp_server_diagnostics (Transact-SQL)](#TitleNum_4)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-tempdb-databasedatabasestempdb-databasemd"></a>1. &nbsp; [Database tempdb](databases/tempdb-database.md)

*Aggiornamento: 20/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 121.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5c8bb5f9c40625aaf955295e5b5d03e4257e6c6b 337555ea28f4c3fdd6b78f1bfb4d62607a6bf92d  (PR=4039  ,  Filename=tempdb-database.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=ef1fa818beea435f58986af3379853dc28f5efd8) -->



**Ottimizzazione delle prestazioni di tempdb**

 Le dimensioni e la posizione fisica del database tempdb possono influire sulle prestazioni di un sistema. Se ad esempio le dimensioni definite per tempdb sono eccessivamente ridotte, il carico di elaborazione del sistema può essere in parte dovuto alla necessità di aumentare automaticamente le dimensioni di tempdb fino a raggiungere quelle necessarie per supportare il carico di lavoro a ogni riavvio dell'istanza di ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)].

 Se possibile, usare l'[inizializzazione immediata dei file di database--../../relational-databases/databases/database-instant-file-initialization.md) per migliorare le prestazioni delle operazioni di aumento delle dimensioni.

 Preallocare lo spazio per tutti i file di tempdb impostando le relative dimensioni su un valore adeguato per il carico di lavoro tipico nell'ambiente. In questo modo il database tempdb non si espanderà con una frequenza eccessiva e le prestazioni non subiranno alterazioni. È opportuno impostare il database tempdb per l'aumento automatico delle dimensioni. Questa funzionalità deve tuttavia essere usata per aumentare lo spazio su disco per le eccezioni non pianificate.

 All'interno di ogni [filegroup--../../relational-databases/databases/database-files-and-filegroups.md#filegroups) i file di dati devono avere le stesse dimensioni, perché ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] usa un algoritmo di riempimento proporzionale che favorisce le allocazioni all'interno di file con maggiore spazio disponibile. La suddivisione di tempdb in più file di dati di dimensioni uguali garantisce un livello elevato di efficienza parallela nelle operazioni che usano tempdb.

 Impostare un valore di aumento delle dimensioni del file tale da evitare aumenti troppo ridotti delle dimensioni dei file del database tempdb. Se l'aumento delle dimensioni dei file è troppo ridotto in confronto alla quantità di dati scritti nel database tempdb, quest'ultimo potrebbe espandersi costantemente. Questo comportamento ha un impatto negativo sulle prestazioni.

 Per controllare i parametri di dimensione e crescita correnti di tempdb, usare la query seguente:
```sql
 SELECT name AS FileName,
    size*1.0/128 AS FileSizeinMB,
    CASE max_size
        WHEN 0 THEN 'Autogrowth is off.'
        WHEN -1 THEN 'Autogrowth is on.'
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-memory-management-architecture-guidememory-management-architecture-guidemd"></a>2. &nbsp; [Guida all'architettura di gestione della memoria](memory-management-architecture-guide.md)

*Aggiornamento: 28/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1) | [Successivo](#TitleNum_3))

<!-- Source markdown line 75.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 dd47431ca47eab16af40e41adaeeaf3fc5fb7461 445f013af3bdad65dd3eaf837db7f744b43e8f97  (PR=4113  ,  Filename=memory-management-architecture-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=28cccac53767db70763e5e705b8cc59a83c77317) -->



Nelle versioni precedenti di SQL Server (..!NCLUDE-NotShown--ssVersion2005--../includes/ssversion2005-md.md)], ..!NCLUDE-NotShown--ssKatmai--../includes/ssKatmai-md.md)] e ..!NCLUDE-NotShown--ssKilimanjaro--../includes/ssKilimanjaro-md.md)]) l'allocazione di memoria veniva gestita con cinque meccanismi diversi:
-  **Allocatore di pagine singole**, che include solo le allocazioni di memoria minori o uguali a 8 KB nel processo di ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)]. Le opzioni di configurazione *max server memory (MB)* e *min server memory (MB)* che determinano i limiti di memoria fisica usata dall'allocatore di pagine singole. Il pool di buffer è contemporaneamente il meccanismo per l'allocazione di pagine singole e il maggiore consumer di allocazioni di pagine singole.
-  **Allocatore di più pagine**, per le allocazioni di memoria che richiedono più di 8 KB.
-  **Allocatore CLR**, che include gli heap CLR SQL e le relative allocazioni globali create durante l'inizializzazione di CLR.
-  Allocazioni di memoria per gli **[stack di thread--../relational-databases/memory-management-architecture-guide.md#stacksizes)** nel processo di ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)].
-  **Allocazioni di Windows dirette**, per le richieste di allocazione di memoria effettuate direttamente da Windows. Sono incluse le allocazioni per l'uso dell'heap di Windows e le allocazioni virtuali dirette effettuate dai moduli caricati nel processo di ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)]. Alcuni esempi di queste richieste di allocazione di memoria sono le allocazioni da DLL di stored procedure estese, gli oggetti creati tramite procedure di automazione (chiamate sp_OA) e le allocazioni dai provider di server collegati.

A partire da ..!NCLUDE-NotShown--ssSQL11--../includes/sssql11-md.md)], le allocazioni di pagine singole, le allocazioni di più pagine e le allocazioni CLR sono tutte consolidate in un **allocatore di pagine di "qualsiasi dimensione"** e sono incluse nei limiti di memoria controllati dalle opzioni di configurazione di *memoria massima del server (MB)* e *memoria minima del server (MB)*. Questa modifica introduce capacità di ridimensionamento più accurate per tutti i requisiti di memoria che passano attraverso lo strumento di gestione della memoria di ..!NCLUDE-NotShown--ssNoVersion--../includes/ssnoversion-md.md)].



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-statisticsstatisticsstatisticsmd"></a>3. &nbsp; [Statistiche](statistics/statistics.md)

*Aggiornamento: 27/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_2) | [Successivo](#TitleNum_4))

<!-- Source markdown line 48.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1dbe3bd6fdfcd27cf4a597cac5a4a09821b51ba7 971cfccf75fbc8842a0ef020a2bc93992c5f4ad9  (PR=4087  ,  Filename=statistics.md  ,  Dirpath=docs\relational-databases\statistics\  ,  MergeCommitSha40=9fbe5403e902eb996bab0b1285cdade281c1cb16) -->



> [!NOTE]
> In ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] gli istogrammi vengono creati solo per una singola colonna, ovvero la prima colonna nel set di colonne chiave dell'oggetto statistiche.

Per creare l'istogramma, Query Optimizer ordina i valori di colonna, calcola il numero di valori che corrispondono a ogni valore distinct di colonna, quindi aggrega i valori di colonna in un massimo di 200 intervalli contigui dell'istogramma. Ogni intervallo dell'istogramma comprende un insieme di valori di colonna seguiti da un valore di colonna pari al limite superiore. Nell'insieme sono inclusi tutti i possibili valori di colonna compresi tra i valori limite, esclusi questi ultimi. Il minore tra i valori di colonna ordinati costituisce il limite superiore per il primo intervallo dell'istogramma.

Più in dettaglio, ..!NCLUDE-NotShown--ssNoVersion--../../includes/ssnoversion-md.md)] crea l'**istogramma** dal set ordinato di valori di colonna in tre passaggi:

- **Inizializzazione dell'istogramma**: nel primo passaggio viene elaborata una sequenza di valori a partire dall'inizio del set ordinato e vengono raccolti fino a 200 valori di *range_high_key*, *equal_rows*, *range_rows* e *distinct_range_rows* (in questo passaggio *range_rows* e *distinct_range_rows* sono sempre pari a zero). Il primo passaggio termina quando è stato esaurito tutto l'input o quando sono stati trovati 200 valori.
- **Analisi con unione di bucket**: nel secondo passaggio viene elaborato ogni valore aggiuntivo della colonna iniziale della chiave delle statistiche in base all'ordinamento. Ogni valore successivo viene aggiunto all'ultimo intervallo o viene creato un nuovo intervallo alla fine (questo è possibile perché i valori di input sono ordinati). Se viene creato un nuovo intervallo, una coppia di intervalli esistenti adiacenti viene compressa in un intervallo singolo. Questa coppia di intervalli viene selezionata per ridurre al minimo la perdita di informazioni. Questo metodo usa un algoritmo per il calcolo della *differenza massima*, per ridurre al minimo il numero di intervalli nell'istogramma, aumentando contemporaneamente la differenza tra i valori limite. Durante questa fase il numero di passaggi dopo la compressione degli intervalli rimane 200.



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-spserverdiagnostics-transact-sqlsystem-stored-proceduressp-server-diagnostics-transact-sqlmd"></a>4. &nbsp; [sp_server_diagnostics (Transact-SQL)](system-stored-procedures/sp-server-diagnostics-transact-sql.md)

*Aggiornamento: 21/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_3))

<!-- Source markdown line 157.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d0d97efbb0b16638d0120af9ac5e66ec3bcfa391 b98735ec26a091f8c8c58ca1790243be7942e038  (PR=4052  ,  Filename=sp-server-diagnostics-transact-sql.md  ,  Dirpath=docs\relational-databases\system-stored-procedures\  ,  MergeCommitSha40=45e4efb7aa828578fe9eb7743a1a3526da719555) -->



La query di esempio seguente legge l'output di riepilogo dalla tabella:
```sql
SELECT create_time,
       component_name,
       state_desc
FROM SpServerDiagnosticsResult;
```

La query di esempio seguente legge parte dell'output dettagliato da ogni componente nella tabella:
```sql
-- system
select data.value('(/system/@systemCpuUtilization)[1]','bigint') as 'System_CPU',
   data.value('(/system/@sqlCpuUtilization)[1]','bigint') as 'SQL_CPU',
   data.value('(/system/@nonYieldingTasksReported)[1]','bigint') as 'NonYielding_Tasks',
   data.value('(/system/@pageFaults)[1]','bigint') as 'Page_Faults',
   data.value('(/system/@latchWarnings)[1]','bigint') as 'Latch_Warnings',
   data.value('(/system/@BadPagesDetected)[1]','bigint') as 'BadPages_Detected',
   data.value('(/system/@BadPagesFixed)[1]','bigint') as 'BadPages_Fixed'
from SpServerDiagnosticsResult
where component_name like 'system'
go

-- Resource Monitor
select data.value('(./Record/ResourceMonitor/Notification)[1]', 'VARCHAR(max)') AS [Notification],
    data.value('(/resource/memoryReport/entry[@description=''Working Set'']/@value)[1]', 'bigint')/1024 AS [SQL_Mem_in_use_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Paging File'']/@value)[1]', 'bigint')/1024 AS [Avail_Pagefile_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Physical Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_Physical_Mem_MB],
    data.value('(/resource/memoryReport/entry[@description=''Available Virtual Memory'']/@value)[1]', 'bigint')/1024 AS [Avail_VAS_MB],
    data.value('(/resource/@lastNotification)[1]','varchar(100)') as 'LastNotification',
    data.value('(/resource/@outOfMemoryExceptions)[1]','bigint') as 'OOM_Exceptions'
from SpServerDiagnosticsResult
where component_name like 'resource'
go

-- Nonpreemptive waits
```







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+14): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1+0): **Analysis Services for SQL (Analysis Services per SQL)** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (87+0): documentazione della **piattaforma di strumenti analitici per SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (5+4): documentazione della **connessione a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1): documentazione del **motore di database di SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (2+2): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (10+9): documentazione di **Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (2+4): documentazione dei **database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (4+2): documentazione di **SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+1): documentazione degli **esempi per SQL Server**](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (21+0): documentazione di **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (5+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+0): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


