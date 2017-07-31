---
title: Aggiornato - docs database relazionali | Documenti Microsoft
description: Visualizzare i frammenti di contenuto aggiornato per la documentazione modificato di recente in, per i database relazionali.
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
ms.date: 07/17/2017
ms.author: genemi
ms.translationtype: HT
ms.sourcegitcommit: 71203bfa7cb4dcd06cc14ad8e49e5bc1113f8605
ms.openlocfilehash: 519fbd2bc596112dbb1c662d76e4aeeb230ffc36
ms.contentlocale: it-it
ms.lasthandoff: 07/31/2017

---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Nuovi e recentemente aggiornato: docs database relazionali



Quasi ogni giorno Microsoft aggiorna alcuni articoli esistenti nel relativo [Docs.Microsoft.com](http://docs.microsoft.com/) sito Web di documentazione. In questo articolo consente di visualizzare estratti dagli articoli aggiornati di recente. Potrebbero anche essere elencati collegamenti a nuovi articoli.

In questo articolo viene generato da un programma che viene eseguito di nuovo periodicamente. In alcuni casi un estratto può apparire con formattazione perfetto, o come markdown nell'articolo di origine. Le immagini non vengono mai visualizzate qui.

Aggiornamenti recenti vengono indicati per il seguente intervallo di date e l'oggetto:



- *Intervallo di date degli aggiornamenti:* &nbsp; **23/05/2017** &nbsp; - &nbsp; **17/07/2017**
- *Area di interesse:* &nbsp; **database relazionali**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Caratteristiche interne di OLTP in memoria di SQL Server per SQL Server 2016](in-memory-oltp/sql-server-in-memory-oltp-internals-for-sql-server-2016.md)
2. [Adaptive query processing in SQL databases](performance/adaptive-query-processing.md) (Elaborazione di query adattive nei database SQL)
3. [Guide to enhancing privacy and addressing GDPR requirements with the Microsoft SQL platform](security/microsoft-sql-and-the-gdpr-requirements.md) (Guida al miglioramento della privacy e ai requisiti GDPR con la piattaforma Microsoft SQL)
4. [sys.pdw_replicated_table_cache_state (Transact-SQL)](system-catalog-views/sys-pdw-replicated-table-cache-state-transact-sql.md)
5. [sys.trusted_assemblies (Transact-SQL)](system-catalog-views/sys-trusted-assemblies-transact-sql.md)
6. [sys.dm_exec_query_parallel_workers (Transact-SQL)](system-dynamic-management-views/sys-dm-exec-query-parallel-workers-transact-sql.md)
7. [sys.sp_add_trusted_assembly (Transact-SQL)](system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md)
8. [sys.sp_drop_trusted_assembly (Transact-SQL)](system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md)




&nbsp;

<a name="compactupdatedlist"/>

## <a name="compact-list-of-articles-updated-recently"></a>Compact elenco degli articoli aggiornato di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione vengono estratti gli aggiornamenti raccolti dagli articoli di cui si sono verificati recentemente un aggiornamento di grandi dimensioni.

Gli estratti visualizzati qui vengono visualizzati separatamente dal relativo contesto semantica corretto Inoltre, talvolta un estratto è separato dalla sintassi markdown importante che la racchiude nell'articolo effettivo. Di conseguenza questi estratti sono solo a scopo generale. Gli estratti consentono solo di sapere se i tuoi interessi garantiscono la necessità di fare clic e visitare l'articolo effettivo.

Per queste e altre ragioni, non copiare da questi estratti di codice e non prendono come verità esatta qualsiasi testo estratto. In alternativa, visitare l'articolo effettivo.



&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-altering-memory-optimized-tablesin-memory-oltpaltering-memory-optimized-tablesmd"></a>1. &nbsp; [Modifica di tabelle ottimizzate per la memoria](in-memory-oltp/altering-memory-optimized-tables.md)

*Aggiornamento: 23/06/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 82.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 8359700b5db24838f1bb273526794c2865bbbe11 41d77cf0bbcf53a1b64d6524a24e5736c5a073da  (PR=2171  ,  Filename=altering-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=7d2dbe0bdc4cbd05f11eacf938b35a9c35ace2e7) -->



**Registrazione di ALTER TABLE in tabelle ottimizzate per la memoria**

In una tabella con ottimizzazione per la memoria, la maggior parte degli scenari ALTER TABLE ora viene eseguita in parallelo, con conseguente ottimizzazione delle operazioni di scrittura nel log delle transazioni. L'ottimizzazione si ottiene registrando nel log delle transazioni solo le modifiche ai metadati. Le operazioni ALTER TABLE seguenti vengono tuttavia eseguite a thread singolo e non sono ottimizzate per il log.

In questo caso l'operazione a thread singolo registrerebbe l'intero contenuto della tabella modificata nel log delle transazioni. Di seguito è riportato un elenco di operazioni a thread singolo:

- Modificare o aggiungere una colonna per usare un tipo LOB (Large Object): nvarchar(max), varchar(max) o varbinary(max).

- Aggiungere o eliminare un indice COLUMNSTORE.

- Quasi qualsiasi cosa che influisca su una [off-row column--../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md).

    - Spostare una colonna dall'interno di righe all'esterno di righe.

    - Spostare una colonna dall'esterno di righe all'interno di righe.

    - Creare una nuova colonna all'esterno di righe.

    - *Eccezione:* il prolungamento di una colonna già all'esterno di righe viene registrato in modo ottimizzato. 
  




&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-table-and-row-size-in-memory-optimized-tablesin-memory-oltptable-and-row-size-in-memory-optimized-tablesmd"></a>2. &nbsp;[Dimensioni di tabelle e righe per le tabelle ottimizzate per la memoria](in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)

*Aggiornamento: 22/06/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1) | [Successivo](#TitleNum_3))

<!-- Source markdown line 114.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 27ce0fa2e7bb464f9c3d6e32dd195de3b79abfcd 0a3cacd86024e2b734704ffd37e55ca0b17a0c94  (PR=2163  ,  Filename=table-and-row-size-in-memory-optimized-tables.md  ,  Dirpath=docs\relational-databases\in-memory-oltp\  ,  MergeCommitSha40=fe6de2b16b9792a5399b1c014af72a2a5ee52377) -->



 
  
 Il calcolo di [row body size] viene descritto nella tabella seguente.  
  
 Le dimensioni del corpo delle righe possono essere considerate da due punti di vista diversi, le dimensioni calcolate e le dimensioni effettive, come illustrato di seguito.  
  
-   Le dimensioni calcolate, indicate con [computed row body size], vengono utilizzate per determinare se il limite di dimensione di 8.060 byte viene superato.  
  
-   Le dimensioni effettive, indicate con [actual row body size], rappresentano le dimensioni di archiviazione effettive del corpo delle righe in memoria e nei file del checkpoint.  
  
 Entrambi i valori di [computed row body size] e [actual row body size] vengono calcolati in modo analogo. L'unica differenza è il calcolo delle dimensioni delle colonne (n)varchar(i) e varbinary(i), come evidenziato nella parte inferiore della tabella seguente. Per le dimensioni calcolate del corpo delle righe viene usata la dimensione dichiarata *i* come dimensione della colonna, mentre per le dimensioni effettive del corpo delle righe viene usata la dimensione effettiva dei dati.  
  
 Nella tabella seguente viene descritto il calcolo delle dimensioni del corpo delle righe, fornito come [actual row body size] = SUM ([size of shallow types) + 2 + 2 * [number of deep type columns].  
  
|Sezione|Dimensione|Commenti|  
|-------------|----------|--------------|  
|Colonne di tipo superficiale|SUM([size of shallow types]). Le dimensioni in byte dei singoli tipi sono le seguenti:<br /><br /> **Bit**: 1<br /><br /> **Tinyint**: 1<br /><br /> **Smallint**: 2<br /><br /> **Int**: 4<br /><br /> **Real**: 4<br /><br /> **Smalldatetime**: 4<br /><br /> **Smallmoney**: 4<br /><br /> **Bigint**: 8<br /><br /> **Datetime**: 8<br /><br /> **Datetime2**: 8<br /><br /> **Float**: 8<br /><br /> **Money**: 8<br /><br /> **Numeric** (precisione <=18): 8<br /><br /> **Time**: 8<br /><br /> **Numeric**(precisione >18): 16<br /><br /> **Uniqueidentifier**: 16||  
|Riempimento delle colonne superficiali|I valori possibili sono:<br /><br /> 1 se esistono colonne di tipo approfondito e le dimensioni totali dei dati delle colonne superficiali sono un numero dispari.<br /><br /> In caso contrario, 0|I tipi approfonditi sono i tipi (var)binary e (n)(var)char.|  




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-post-migration-validation-and-optimization-guidepost-migration-validation-and-optimization-guidemd"></a>3. &nbsp;[Guida di ottimizzazione e convalida post-migrazione](post-migration-validation-and-optimization-guide.md)

*Aggiornamento: 21/06/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_2) | [Successivo](#TitleNum_4))

<!-- Source markdown line 27.  ms.author= "harinid".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 faa2e3dd8be3aeb475bf8c7f71617ebf17969892 f2760dfecda10baeb121929b72a4d8164e81185b  (PR=2126  ,  Filename=post-migration-validation-and-optimization-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=dcbeda6b8372b358b6497f78d6139cad91c8097c) -->



Di seguito sono riportati alcuni scenari comuni relativi alle prestazioni rilevati dopo la migrazione alla piattaforma [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] e viene indicato come risolverli. Sono inclusi scenari specifici della migrazione da [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] (da versioni precedenti a versioni più recenti), nonché da piattaforme non Microsoft (ad esempio Oracle, DB2, MySQL e Sybase) a [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)].

**<a name="CEUpgrade"></a> Regressioni delle query dovute a modifiche della versione CE**


**Si applica a:** migrazione da [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] a [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)].

Quando si esegue la migrazione da una versione precedente di [!INCLUDE[ssNoVersion--../includes/ssnoversion-md.md)] a [!INCLUDE[ssSQL14--../includes/sssql14-md.md)] o versione successiva e l'aggiornamento di [database compatibility level--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) alla versione più recente, un carico di lavoro può essere esposto al rischio di regressione delle prestazioni.

Ciò avviene perché a partire da [!INCLUDE[ssSQL14--../includes/sssql14-md.md)] tutte le modifiche di Query Optimizer sono legate al [database compatibility level--../relational-databases/databases/view-or-change-the-compatibility-level-of-a-database.md) più recente, quindi i piani non vengono modificati esattamente in corrispondenza del punto di aggiornamento, ma quando un utente passa dall'opzione di database `COMPATIBILITY_LEVEL` a una più recente. Questa funzionalità, in combinazione con Archivio query, offre un alto livello di controllo sulle prestazioni delle query nel processo di aggiornamento. 

Per altre informazioni sulle modifiche di Query Optimizer introdotte in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], vedere la sezione relativa all'[ottimizzazione dei piani di query con la stima di cardinalità di SQL Server 2014](http://msdn.microsoft.com/library/dn673537.aspx).




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-sysquerystoreplan-transact-sqlsystem-catalog-viewssys-query-store-plan-transact-sqlmd"></a>4. &nbsp; [sys.query_store_plan (Transact-SQL)](system-catalog-views/sys-query-store-plan-transact-sql.md)

*Aggiornamento: 05/06/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Precedente](#TitleNum_3))

<!-- Source markdown line 58.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 1b77e34309ba7033578b3c82ed83c8c2fbc93e24 ce4ade9ab906c35cb87068a1fb91c4e1d7549aac  (PR=1940  ,  Filename=sys-query-store-plan-transact-sql.md  ,  Dirpath=docs\relational-databases\system-catalog-views\  ,  MergeCommitSha40=1d363db8e8bd0e1460cdea3c3a7add68e48714c9) -->



**Limitazioni per l'uso forzato dei piani**

Query Store è dotato di un meccanismo per imporre a Query Optimizer l'uso di determinati piani di esecuzione. Esistono tuttavia alcune limitazioni che possono impedire l'imposizione di un piano. 

In primo luogo, se il piano contiene i costrutti seguenti:
* Istruzione Insert bulk.
* Istruzione Insert bulk.
* Riferimento a una tabella esterna
* Query distribuita o operazioni full-text
* Uso di query globali 
* Cursori
* Specifica di join a stella non valida 

In secondo luogo, quando gli oggetti su cui si basa il piano non sono più disponibili:
* Database (se il database da cui ha avuto origine il piano non esiste più)
* Indice (non più esistente o disabilitato)

Infine, problemi del piano stesso:
* Piano non valido per query
* Numero di operazioni consentite per Query Optimizer superato
* XML del piano formato in modo non corretto





<a name="similars2"/>

&nbsp;

## <a name="similar-articles"></a>Articoli simili

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno dello stesso repository GitHub: [MicrosoftDocs/**sql-docs-pr**](https://github.com/microsoftdocs/sql-docs-pr/).

<!--  20170717-1101  -->

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (4+4): **Advanced Analytics per SQL** Docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (2+0): **Analysis Services per SQL** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (1+2): **Connetti a SQL Server** Docs](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (6+0): **Motore di database per SQL** Docs](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (13+2): **Linux per SQL** Docs](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (1+0): **Master Data Services (MDS) per SQL** Docs](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (1+0): **ODBC (Open Database Connectivity) per SQL** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (8+4): **Database relazionali per SQL** Docs](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (2+2): **Microsoft SQL Server** Docs](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (1+0): **Transact-SQL** Docs](../t-sql/new-updated-t-sql.md)
- [Nuovo + aggiornato (1+0): **Strumenti per SQL** Docs](../tools/new-updated-tools.md)


#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): **Integration Services per SQL** Docs](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): **Reporting Services per SQL** Docs](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (0+0): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


&nbsp;


