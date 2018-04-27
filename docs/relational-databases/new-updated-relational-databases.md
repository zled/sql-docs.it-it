---
title: 'Articolo aggiornato: documentazione dei database relazionali | Microsoft Docs'
description: Visualizza frammenti di contenuto aggiornato relativi alle modifiche recenti alla documentazione dei database relazionali.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.prod_service: sql
ms.component: relational-databases
ms.date: 02/03/2018
ms.openlocfilehash: fc37abbb88aa597a6173fa5579fa320e0024581f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="new-and-recently-updated-relational-databases-docs"></a>Articoli nuovi e aggiornati di recente: documentazione dei database relazionali



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **03/12/2017** &nbsp; - &nbsp; **03/02/2018**
- *Area di interesse:* &nbsp; **database relazionali**.




&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Archiviare documenti JSON in SQL Server o nel database SQL](json/store-json-documents-in-sql-tables.md)
2. [Valutazione della vulnerabilità SQL](security/sql-vulnerability-assessment.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Inizializzazione di file di database](#TitleNum_1)
2. [Database tempdb](#TitleNum_2)
3. [Dati JSON in SQL Server](#TitleNum_3)
4. [Lezione 1: Connessione al motore di database](#TitleNum_4)
5. [Gestione delle dimensioni del file di log delle transazioni](#TitleNum_5)
6. [bcp_bind](#TitleNum_6)
7. [Guida per la progettazione di indici di SQL Server](#TitleNum_7)
8. [sp_execute_external_script (Transact-SQL)](#TitleNum_8)
9. [Creare chiavi primarie](#TitleNum_9)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-database-file-initializationdatabasesdatabase-instant-file-initializationmd"></a>1. &nbsp;[Inizializzazione di file di database](databases/database-instant-file-initialization.md)

*Aggiornamento: 23/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Successivo](#TitleNum_2))

<!-- Source markdown line 81.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c5f2aa53a8b43d4c43e0602cf945cb7c7028a27d 04c261c6588af1f53cda2fce3e9a86167c50b686  (PR=4702  ,  Filename=database-instant-file-initialization.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=3206a31870f8febab7d1718fa59fe0590d4d45db) -->



```
Database Instant File Initialization: disabled. For security and performance considerations see the topic 'Database Instant File Initialization' in SQL Server Books Online. This is an informational message only. No user action is required.
```

**Si applica a:** SQL Server (da SQL Server 2012 SP4, SQL Server 2014 SP2 e SQL Server 2016 fino a SQL Server 2017)

**Considerazioni sulla sicurezza**

Se si utilizza l'inizializzazione immediata dei file, poiché il contenuto eliminato del disco viene sovrascritto solo quando vengono scritti nuovi dati nei file, il contenuto eliminato potrebbe essere accessibile a utenti o servizi non autorizzati, finché non vengono eseguite altre scritture dati in tale area specifica del file di dati. Finché il file di database è collegato all'istanza di SQL Server, questo rischio di diffusione di informazioni è ridotto dall'elenco di controllo di accesso discrezionale (DACL) per il file. Questo elenco consente l'accesso al file solo all'account del servizio SQL Server e all'amministratore locale. Quando il file viene scollegato, tuttavia, diventa accessibile a un utente o a un servizio privo del diritto SE\_MANAGE\_VOLUME_NAME. Una considerazione di questo tipo è necessaria quando viene eseguito un backup del database: se il file di backup non è protetto con un elenco di controllo di accesso discrezionale (DACL) appropriato, il contenuto eliminato può diventare disponibile a un utente o a un servizio non autorizzato.

Tenere presente anche che quando un file usa l'inizializzazione immediata, un amministratore SQL Server può potenzialmente accedere ai contenuti delle pagine non elaborati e visualizzare i contenuti precedentemente eliminati.

Se i file di database sono ospitati in una rete di archiviazione, è anche possibile che la rete di archiviazione visualizzi sempre le pagine nuove come pagine preinizializzate e non sia necessario che il sistema operativo ne esegua nuovamente l'inizializzazione.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-tempdb-databasedatabasestempdb-databasemd"></a>2. &nbsp;[Database tempdb](databases/tempdb-database.md)

*Aggiornamento: 17/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_1) | [Successivo](#TitleNum_3))

<!-- Source markdown line 100.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 337555ea28f4c3fdd6b78f1bfb4d62607a6bf92d 3257c92d6e2a88968fc44e5f6262c02cd0624635  (PR=0  ,  Filename=tempdb-database.md  ,  Dirpath=docs\relational-databases\databases\  ,  MergeCommitSha40=45e6082acc29ba306525e7c08d2c22cc2b86eec3) -->



 Per una descrizione di queste opzioni di database, vedere [Opzioni ALTER DATABASE SET (Transact-SQL)](databases/../../t-sql/statements/alter-database-transact-sql-set-options.md).

**Database tempdb nel database SQL**


|SLO|Dimensioni massime del file di dati tempdb (MB)|N. di file di dati tempdb|Dimensioni massime dei dati tempdb (MB)|
|---|---:|---:|---:|
|Standard|14.225|1|14.225|
|S0|14.225|1|14.225|
|S1|14.225|1|14.225|
|S2|14.225| 1|14.225|
|S3|32.768|1|32.768|
|S4|32.768|2|65,536|
|S6|32.768|3|98.304|
|S7|32.768|6|196.608|
|S9|32.768|12|393.216|
|S12|32.768|12|393.216|
|P1|32.768|12|393.216|
|P2|32.768|12|393.216|
|P4|32.768|12|393.216|
|P6|32.768|12|393.216|
|P11|32.768|12|393.216|
|P15|32.768|12|393.216|
|Pool elastici Premium (tutte le configurazioni DTU)|14.225|12|170.700|
|Pool elastici Standard (tutte le configurazioni DTU)|14.225|12|170.700|
|Pool elastici Basic (tutte le configurazioni DTU)|14.225|12|170.700|
||||




&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-json-data-in-sql-serverjsonjson-data-sql-servermd"></a>3. &nbsp;[Dati JSON in SQL Server](json/json-data-sql-server.md)

*Aggiornamento: 01/02/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_2) | [Successivo](#TitleNum_4))

<!-- Source markdown line 233.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 62dd9c68d8cb72d6bf51b941a0731224514f0a7f 19e276637a463b412f2c29a84f9fb7d0b0f5fcc5  (PR=4783  ,  Filename=json-data-sql-server.md  ,  Dirpath=docs\relational-databases\json\  ,  MergeCommitSha40=73f18ae24a9a48234bf997ee9a2ef441bc4918b9) -->



-   [Load GeoJSON data into SQL Server 2016](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/01/05/loading-geojson-data-into-sql-server/) (Caricare i dati GeoJSON in SQL Server 2016)

**Analizzare i dati JSON con query SQL**

Se è necessario filtrare o aggregare dati JSON per la creazione di report, è possibile usare **OPENJSON** per trasformare i dati JSON in formato relazionale. È quindi possibile usare le funzioni predefinite e Transact-SQL standard per preparare i report.

```
SELECT Tab.Id, SalesOrderJsonData.Customer, SalesOrderJsonData.Date
FROM   SalesOrderRecord AS Tab
          CROSS APPLY
     OPENJSON (Tab.json, N'$.Orders.OrdersArray')
           WITH (
              Number   varchar(200) N'$.Order.Number',
              Date     datetime     N'$.Order.Date',
              Customer varchar(200) N'$.AccountNumber',
              Quantity int          N'$.Item.Quantity'
           )
  AS SalesOrderJsonData
WHERE JSON_VALUE(Tab.json, '$.Status') = N'Closed'
ORDER BY JSON_VALUE(Tab.json, '$.Group'), Tab.DateModified
```



&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-lesson-1-connecting-to-the-database-enginelesson-1-connecting-to-the-database-enginemd"></a>4. &nbsp; [Lezione 1: Connessione al motore di database](lesson-1-connecting-to-the-database-engine.md)

*Aggiornamento: 13/12/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_3) | [Successivo](#TitleNum_5))

<!-- Source markdown line 79.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3c070935895450fd2ea054e2be9e1c48f7dc2b6c 0c386e3d47fb7f8f1e63b9301f0cafec2bc88ab0  (PR=4282  ,  Filename=lesson-1-connecting-to-the-database-engine.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=6e016a4ffd28b09456008f40ff88aef3d911c7ba) -->



2.  Selezionare **Motore di database**.

    ![object-explorer](../relational-databases/media/object-explorer.png)

3.  Nella casella **Nome server** digitare il nome dell'istanza del motore di database. Per l'istanza predefinita di SQL Server il nome del server è il nome del computer. Per un'istanza denominata di SQL Server, il nome del server è *<nome_computer>***\\***<nome_istanza>*, ad esempio **ACCTG_SRVR\SQLEXPRESS**. Lo screenshot seguente mostra la connessione all'istanza predefinita (non denominata) di SQL Server in un computer denominato 'PracticeComputer'. L'utente attualmente connesso a Windows è Mary dal dominio Contoso. Quando si usa l'autenticazione di Windows non è possibile modificare il nome utente.

    ![connect-to-server](../relational-databases/media/connect-to-server.png)

4.  Fare clic su **Connetti**.

> [!NOTE]
> In questa esercitazione si presuppone che non si abbia familiarità con SQL Server e che non si abbiano particolari problemi di connessione. Questa esercitazione è semplice e dovrebbe essere sufficiente per la maggior parte degli utenti. Per istruzioni dettagliate per la risoluzione dei problemi, vedere [Risolvere i problemi di connessione al motore di database di SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md).

**<a name="additional"></a>Autorizzazione di connessioni aggiuntive**

Dopo avere stabilito la connessione a SQL Server come amministratore, una delle prime attività da svolgere consiste nell'autorizzare altri utenti a connettersi. A questo scopo è necessario creare un account di accesso e autorizzare tale account ad accedere a un database come utente. È possibile configurare account di accesso con autenticazione di Windows, che usano le credenziali di Windows, o account di accesso con autenticazione di SQL Server, che archiviano le informazioni autenticate in SQL Server e sono indipendenti dalle credenziali di Windows. Se possibile, utilizzare l'autenticazione di Windows.



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-manage-the-size-of-the-transaction-log-filelogsmanage-the-size-of-the-transaction-log-filemd"></a>5. &nbsp;[Gestire le dimensioni del file registro transazioni](logs/manage-the-size-of-the-transaction-log-file.md)

*Aggiornamento: 17/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_4) | [Successivo](#TitleNum_6))

<!-- Source markdown line 105.  ms.author= "jhubbard".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5847b31cf8f6003a380f0c8aaa289efdc55be678 84e45320d81db218cde17fbf8b9668a9ac3805a7  (PR=0  ,  Filename=manage-the-size-of-the-transaction-log-file.md  ,  Dirpath=docs\relational-databases\logs\  ,  MergeCommitSha40=45e6082acc29ba306525e7c08d2c22cc2b86eec3) -->



-   Un incremento della crescita ridotto può generare molti file [VLF](logs/../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) piccoli e ridurre le prestazioni. Per determinare la distribuzione dei file di log virtuali ottimale per le dimensioni correnti del log delle transazioni di tutti i database in un'istanza specifica e gli incrementi della crescita necessari per ottenere le dimensioni richieste, vedere questo [script](http://github.com/Microsoft/tigertoolbox/tree/master/Fixing-VLFs).

-   Un incremento della crescita elevato può generare pochi file [VLF](logs/../../relational-databases/sql-server-transaction-log-architecture-and-management-guide.md#physical_arch) di grandi dimensioni e ridurre a sua volta le prestazioni. Per determinare la distribuzione dei file di log virtuali ottimale per le dimensioni correnti del log delle transazioni di tutti i database in un'istanza specifica e gli incrementi della crescita necessari per ottenere le dimensioni richieste, vedere questo [script](http://github.com/Microsoft/tigertoolbox/tree/master/Fixing-VLFs).

-   Anche con l'aumento automatico attivato è possibile che si riceva un messaggio indicante che il log delle transazioni è pieno, se questo non può crescere a sufficienza per soddisfare le esigenze della query. Per altre informazioni su come modificare l'incremento della crescita, vedere [Opzioni per file e filegroup ALTER DATABASE &#40;Transact-SQL&#41;](logs/../../t-sql/statements/alter-database-transact-sql-file-and-filegroup-options.md)

-   La presenza di più file di log in un database non migliora le prestazioni, perché i file di log delle transazioni non usano il [riempimento proporzionale](logs/../../relational-databases/pages-and-extents-architecture-guide.md#ProportionalFill) come i file di dati nello stesso gruppo di file.

-   È possibile impostare i file di log in modo che vengano compattati automaticamente. Tuttavia questa impostazione **è sconsigliata** e la proprietà del database **auto_shrink** è FALSE per impostazione predefinita. Se **auto_shrink** è impostata su TRUE, la compattazione automatica riduce le dimensioni di un file solo quando più del 25% dello spazio del file risulta inutilizzato.



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-bcpbindnative-client-odbc-extensions-bulk-copy-functionsbcp-bindmd"></a>6. &nbsp; [bcp_bind](native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)

*Aggiornamento: 30/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_5) | [Successivo](#TitleNum_7))

<!-- Source markdown line 127.  ms.author= "genemi".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d50791cef948ce8b3066438e317ab4d34d535258 e6f70559e7237cfc86dfc5746d218c08bec52af6  (PR=4762  ,  Filename=bcp-bind.md  ,  Dirpath=docs\relational-databases\native-client-odbc-extensions-bulk-copy-functions\  ,  MergeCommitSha40=60006e90d03fdb75b282bbc0dad3d40571bacacc) -->



 La tabella seguente elenca i tipi di dati enumerati validi e i tipi di dati ODBC C corrispondenti.

|eDataType|Tipo C|
|-----------------------|------------|
|SQLTEXT|char *|
|SQLNTEXT|wchar_t *|
|SQLCHARACTER|char *|
|SQLBIGCHAR|char *|
|SQLVARCHAR|char *|
|SQLBIGVARCHAR|char *|
|SQLNCHAR|wchar_t *|
|SQLNVARCHAR|wchar_t *|
|SQLBINARY|unsigned char *|
|SQLBIGBINARY|unsigned char *|
|SQLVARBINARY|unsigned char *|
|SQLBIGVARBINARY|unsigned char *|
|SQLBIT|char|
|SQLBITN|char|
|SQLINT1|char|
|SQLINT2|short int|
|SQLINT4|INT|
|SQLINT8|_int64|
|SQLINTN|*cbIndicator*<br /> 1: SQLINT1<br /> 2: SQLINT2<br /> 4: SQLINT4<br /> 8: SQLINT8|
|SQLFLT4|FLOAT|
|SQLFLT8|FLOAT|
|SQLFLTN|*cbIndicator*<br /> 4: SQLFLT4<br /> 8: SQLFLT8|
|SQLDECIMALN|SQL_NUMERIC_STRUCT|
|SQLNUMERICN|SQL_NUMERIC_STRUCT|
|SQLMONEY|DBMONEY|
|SQLMONEY4|DBMONEY4|
|SQLMONEYN|*cbIndicator*<br /> 4: SQLMONEY4<br /> 8: SQLMONEY|
|SQLTIMEN|SQL_SS_TIME2_STRUCT|
|SQLDATEN|SQL_DATE_STRUCT|
|SQLDATETIM4|DBDATETIM4|
|SQLDATETIME|DBDATETIME|
|SQLDATETIMN|*cbIndicator*<br /> 4: SQLDATETIM4<br /> 8: SQLDATETIME|
|SQLDATETIME2N|SQL_TIMESTAMP_STRUCT|
|SQLDATETIMEOFFSETN|SQL_SS_TIMESTAMPOFFSET_STRUCT|
|SQLIMAGE|unsigned char *|
|SQLUDT|unsigned char *|
|SQLUNIQUEID|SQLGUID|
|SQLVARIANT|*Qualsiasi tipo di dati ad eccezione di:*<br />-   text<br />-   ntext<br />-   image<br />-   varchar(max)<br />-   varbinary(max)<br />-   nvarchar(max)<br />-   xml<br />-   timestamp|
|SQLXML|*Tipi di dati C supportati:*<br />-   char*<br />-   wchar_t *<br />-   unsigned char *|



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-sql-server-index-design-guidesql-server-index-design-guidemd"></a>7. &nbsp;[Guida per la progettazione di indici di SQL Server](sql-server-index-design-guide.md)

*Aggiornamento: 02/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_6) | [Successivo](#TitleNum_8))

<!-- Source markdown line 700.  ms.author= "rickbyh".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bd09c9e66cd3cf5f3ebebe7ffa6e937978353169 8e5cbbf0063971676a8bafefba75aa5c7c28be61  (PR=0  ,  Filename=sql-server-index-design-guide.md  ,  Dirpath=docs\relational-databases\  ,  MergeCommitSha40=74daee358fef75a25d75c69d971d08536c5bd2be) -->



A partire da SQL Server 2016, è possibile creare un indice **columnstore non cluster aggiornabile in una tabella rowstore**. L'indice columnstore archivia una copia dei dati, pertanto è necessario spazio di archiviazione aggiuntivo. Tuttavia, i dati nell'indice columnstore verranno compressi fino a ottenere dimensioni minori rispetto a quanto richiesto per la tabella del rowstore.  In questo modo è possibile eseguire allo stesso tempo analisi sull'indice columnstore e transazioni sull'indice rowstore. Il columnstore viene aggiornato quando i dati nella tabella rowstore vengono modificati. In questo modo entrambi gli indici possono usare gli stessi dati.

A partire da SQL Server 2016, è possibile avere **uno o più indici rowstore non cluster per un indice columnstore**. Ciò consente di eseguire ricerche efficienti all'interno delle tabelle del columnstore sottostante. Sono disponibili anche altre opzioni. È possibile, ad esempio, applicare un vincolo di chiave primaria tramite un vincolo UNIQUE nella tabella rowstore. Di conseguenza, poiché non è possibile inserire un valore non univoco nella tabella rowstore, SQL Server non può inserire il valore nel columnstore.

**Considerazioni sulle prestazioni**


-   La definizione degli indici columnstore non cluster supporta l'uso di una condizione filtrata. Per ridurre al minimo l'impatto sulle prestazioni conseguente all'aggiunta di un indice columnstore in una tabella OLTP, usare una condizione filtrata per creare un indice columnstore non cluster solo sui dati usati meno di frequente del carico di lavoro operativo.

-   Una tabella in memoria può avere un solo indice columnstore. È possibile crearlo durante la creazione della tabella o aggiungerlo in un secondo momento con [ALTER TABLE &#40;Transact-SQL&#41;](../t-sql/statements/alter-table-transact-sql.md). Prima di SQL Server 2016, solamente una tabella basata su disco poteva avere un indice columnstore.

Per altre informazioni, vedere [Indici columnstore - Prestazioni delle query ](../relational-databases/indexes/columnstore-indexes-query-performance.md).

**Linee guida per la progettazione**


-   Una tabella rowstore può avere un solo indice columnstore non cluster aggiornabile. Prima di SQL Server 2014, l'indice columnstore non cluster era un indice di sola lettura.



&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-spexecuteexternalscript-transact-sqlsystem-stored-proceduressp-execute-external-script-transact-sqlmd"></a>8. &nbsp; [sp_execute_external_script (Transact-SQL)](system-stored-procedures/sp-execute-external-script-transact-sql.md)

*Aggiornamento: 23/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_7) | [Successivo](#TitleNum_9))

<!-- Source markdown line 207.  ms.author= "edmaca".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0ee4d591ae9d9a5c015eec98aad9ccbb86268761 ac9b439c23ffae5fcc77639de6ff955763cf5844  (PR=4696  ,  Filename=sp-execute-external-script-transact-sql.md  ,  Dirpath=docs\relational-databases\system-stored-procedures\  ,  MergeCommitSha40=d7dcbcebbf416298f838a39dd5de6a46ca9f77aa) -->



Per generare un modello simile tramite Python, è necessario modificare l'identificatore del linguaggio da `@language=N'R'` a `@language = N'Python'` e apportare le modifiche necessarie all'argomento `@script`. In caso contrario, tutti i parametri funzionano allo stesso modo di R.

**C. Creare un modello Python e generare punteggi da esso**


Questo esempio illustra come usare sp\_execute\_external\_script per generare punteggi in un modello Python semplice.

```
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

**Input query to generate the customer data**

DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders`

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

**Get data from input query**

customer_data = my_input_data

**Define the model**

n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Le intestazioni di colonna usate nel codice Python non vengono trasmesse a SQL Server. Usare quindi l'istruzione WITH RESULTS per specificare i nomi di colonna e i tipi di dati che SQL deve usare.

Per il punteggio, è anche possibile usare la funzione nativa [PREDICT](system-stored-procedures/../../t-sql/queries/predict-transact-sql.md), che è in genere più veloce, perché consente di evitare la chiamata al runtime di Python o R.




&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-create-primary-keystablescreate-primary-keysmd"></a>9. &nbsp;[Creare chiavi primarie](tables/create-primary-keys.md)

*Aggiornamento: 18/01/2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_8))

<!-- Source markdown line 102.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 d18b485f314cc005d624cab8a51650d3b8f55f89 9bd2e9453206e8940d30b0a01c43f9d8e1aed606  (PR=4652  ,  Filename=create-primary-keys.md  ,  Dirpath=docs\relational-databases\tables\  ,  MergeCommitSha40=6b4aae3706247ce9b311682774b13ac067f60a79) -->



**Per creare una chiave primaria con un indice non cluster in una nuova tabella**


1.  In **Esplora oggetti** connettersi a un'istanza del motore di database.

2.  Sulla barra Standard fare clic su **Nuova query**.

3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Nell'esempio si crea una tabella e si definisce una chiave primaria nella colonna `CustomerID` e un indice cluster in `TransactionID`.

```
    USE AdventureWorks2012;
    GO
    CREATE TABLE Production.TransactionHistoryArchive1
    (
       CustomerID uniqueidentifier DEFAULT NEWSEQUENTIALID(),
       TransactionID int IDENTITY (1,1) NOT NULL,
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY NONCLUSTERED (uniqueidentifier)
    );
    GO

    -- Now add the clustered index
    CREATE CLUSTERED INDEX CIX_TransactionID ON Production.TransactionHistoryArchive1 (TransactionID);
    GO
```







## <a name="similar-articles-about-new-or-updated-articles"></a>Articoli simili su articoli nuovi o aggiornati

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).


#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Aree di interesse *con* articoli nuovi o aggiornati di recente


- [Nuovo + aggiornato (1+3):&nbsp; documentazione di **Advanced Analytics per SQL** ](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **piattaforma di strumenti analitici per SQL** ](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione della **connessione a SQL Server** ](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione del **motore di database di SQL Server** ](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (12+1): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (6+2):&nbsp; documentazione di **Linux per SQL Server** ](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (15+0):**documentazione di**PowerShell per SQL Server](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (2+9):&nbsp; documentazione dei **database relazionali per SQL Server** ](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (1+0):&nbsp; documentazione di **SQL Server Reporting Services** ](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di **SQL Operations Studio** ](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (1+1):&nbsp; documentazione di **Microsoft SQL Server** ](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1):&nbsp; documentazione di **SQL Server Data Tools (SSDT)** ](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+2):&nbsp; documentazione di **SQL Server Management Studio (SSMS)** ](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2):&nbsp; documentazione di **Transact-SQL** ](../t-sql/new-updated-t-sql.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Aree di interesse *senza* articoli nuovi o aggiornati di recente


- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): documentazione di **Analysis Services per SQL**](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **Samples for SQL (Esempi per SQL)** Docs](../samples/new-updated-samples.md)
- [Nuovo + aggiornato (0+0): **SQL Server Migration Assistant (SSMA)** Docs](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


