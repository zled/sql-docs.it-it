---
title: CREATE EXTERNAL TABLE AS SELECT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.service: sql-data-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATE EXTERNAL TABLE AS SELECT
- CREATE_EXTERNAL_TABLE_AS_SELECT
- CREATE EXTERNAL TABLE AS SELECT_TSQL
helpviewer_keywords:
- External, table
- PolyBase, external table
- External, table create as select
- PolyBase, create table as select
ms.assetid: 32dfe254-6df7-4437-bfd6-ca7d37557b0a
caps.latest.revision: 16
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 716c0fdaa701865e8d35154cd19068051e0ab017
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-external-table-as-select-transact-sql"></a>CREATE EXTERNAL TABLE AS SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Crea una tabella esterna, quindi Esporta, in parallelo, i risultati di una [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione SELECT in Hadoop o Blob di archiviazione di Azure.  
  
 Utilizzare l'istruzione CREATE EXTERNAL tabella AS selezionare (CETAS):  
  
-   Esportare una tabella di database in archiviazione blob di Hadoop o Azure.  
  
-   Importare dati da Hadoop o Azure nell'archivio blob e archiviarla nel database.  
  
-   Eseguire query sui dati dall'archiviazione blob di Hadoop o Azure, creare un join con tabelle di database relazionale e scrivere i risultati Hadoop o Azure nell'archivio blob.  
  
-   Eseguire query sui dati dall'archiviazione blob di Hadoop o Azure, Trasforma utilizzando le funzionalità di elaborazione del database e write-back in Hadoop o Azure nell'archivio blob.  
  
 Per altre informazioni, vedere [Get started with PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)(Introduzione a PolyBase).  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE EXTERNAL TABLE [ [database_name  . [ schema_name ] . ] | schema_name . ] table_name   
    WITH (   
        LOCATION = 'hdfs_folder',  
        DATA_SOURCE = external_data_source_name,  
        FILE_FORMAT = external_file_format_name  
        [ , <reject_options> [ ,...n ] ]  
    )  
    AS <select_statement>  
[;]  
  
<reject_options> ::=  
{  
    | REJECT_TYPE = value | percentage  
    | REJECT_VALUE = reject_value  
    | REJECT_SAMPLE_VALUE = reject_sample_value  
}  
  
<select_statement> ::=  
    [ WITH <common_table_expression> [ ,...n ] ]  
    SELECT <select_criteria>  
```  
  
## <a name="arguments"></a>Argomenti  
 [[ *database_name* . [ *schema_name* ]. ] | *schema_name* . ] *table_name*  
 Uno a tre - nome parte della tabella da creare nel database. Per una tabella esterna, solo i metadati della tabella sono archiviato nel database relazionale.  
  
 PERCORSO = '*hdfs_folder*'  
 Specifica la posizione in cui scrivere i risultati dell'istruzione SELECT nell'origine dati esterna. Il percorso è un nome di cartella e, facoltativamente, può includere un percorso relativo alla cartella radice del Hadoop Cluster o Blob di archiviazione di Azure.  PolyBase creerà il percorso e la cartella se non esiste già.  
  
 Vengono scritti i file esterni *hdfs_folder* e denominato *Queryid_date_time_id*, dove *ID* è un identificatore incrementale e *formato* è il formato dei dati esportati. Ad esempio, QID776_20160130_182739_0.orc.  
  
 DATA_SOURCE = *external_data_source_name*  
 Specifica il nome dell'oggetto di origine dati esterna che contiene il percorso in cui i dati esterni archiviati sono o saranno archiviati. Il percorso è un Hadoop Cluster o un Blob di archiviazione di Azure. Per creare un'origine dati esterna, utilizzare [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
 FILE_FORMAT = *external_file_format_name*  
 Specifica il nome dell'oggetto formato di file esterno che contiene il formato del file di dati esterno. Per creare un formato di file esterno, usare [CREATE EXTERNAL FILE FORMAT &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-file-format-transact-sql.md).  
  
 Rifiutare opzioni  
 Le opzioni di rifiuto non si applicano al momento che questa istruzione CREATE EXTERNAL TABLE AS SELECT viene eseguita. Al contrario, vengono specificati qui in modo che il database può utilizzare in un secondo momento quando importa i dati dalla tabella esterna. In un secondo momento, quando l'istruzione CREATE TABLE AS SELECT seleziona dati dalla tabella esterna, verranno utilizzate dal database le opzioni di rifiuti per determinare il numero o la percentuale di righe con errori di importazione prima di interrompere l'importazione.  
  
 REJECT_VALUE = *reject_value*  
 Specifica il valore o la percentuale di righe con errori di importazione prima di database consente di arrestare l'importazione.  
  
 REJECT_TYPE = **valore** | percentuale  
 Chiarisce se l'opzione REJECT_VALUE è specificata come valore letterale o percentuale.  
  
 Valore  
 REJECT_VALUE è un valore letterale, non una percentuale.  Il database verrà arrestato l'importazione delle righe dal file di dati esterno quando supera il numero di righe con errori *reject_value*.  
  
 Ad esempio, se REJECT_VALUE = 5 e REJECT_TYPE = valore, il database verrà arrestato l'importazione di righe dopo 5 righe impossibili da importare.  
  
 Percentuale  
 REJECT_VALUE è una percentuale, non un valore letterale. Il database verrà arrestato l'importazione di righe dall'esterno del file di dati quando il *percentuale* di righe con errori supera *reject_value*. La percentuale di righe con errori viene calcolata a intervalli.  
  
 REJECT_SAMPLE_VALUE = *reject_sample_value*  
 Obbligatorio quando REJECT_TYPE = percentuale, consente di specificare il numero di righe per tentare di importare prima che il database ricalcoli la percentuale di righe con errori.  
  
 Ad esempio, se REJECT_SAMPLE_VALUE = 1000, il database verrà calcolata la percentuale di righe con errori dopo che ha tentato di importare 1000 righe dal file di dati esterno. Se la percentuale di righe con errori è inferiore a *reject_value*, il database verrà eseguito un tentativo di caricare un altro 1000 righe. Il database continua a ricalcolare la percentuale di righe con esito negativo dopo il tentativo di importare ogni 1000 righe di aggiuntive.  
  
> [!NOTE]  
>  Poiché il database calcola la percentuale di righe con esito negativo a intervalli, la percentuale effettiva di righe può superare *reject_value*.  
  
 Esempio:  
  
 Questo esempio viene illustrato come le tre opzioni di rifiuto interagiscono tra loro. Ad esempio, se REJECT_TYPE = percentuale, REJECT_VALUE = 30 e REJECT_SAMPLE_VALUE = 100, potrebbe verificarsi il seguente scenario:  
  
-   Il database tenta di caricare le prime 100 righe; 25 avranno esito negativo e 75 esito positivo.  
  
-   Percentuale di righe con errori viene calcolato come 25%, che è minore del valore di rifiuto pari al 30%. Pertanto, non è necessario interrompere il carico.  
  
-   Il database tenta di caricare le righe successive 100; Questa volta 25 esito positivo e 75 esito negativo.  
  
-   Percentuale di righe con errori viene ricalcolato al 50%. La percentuale di righe con errori ha superato il valore di rifiuto di 30%.  
  
-   Il caricamento non riesce con righe 50% non è riuscita dopo il tentativo di caricamento di 200 righe, che è maggiore del limite di 30% specificato.  
  
 CON *common_table_expression*  
 Indica un set di risultati denominato temporaneo, noto come espressione di tabella comune (CTE). Per ulteriori informazioni, vedere [con common_table_expression &#40; Transact-SQL &#41; ](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 Selezionare \<select_criteria > consente di popolare la nuova tabella con i risultati da un'istruzione SELECT. *select_criteria* è il corpo dell'istruzione SELECT che determina i dati da copiare nella nuova tabella. Per informazioni sulle istruzioni SELECT, vedere [SELECT &#40; Transact-SQL &#41; ](../../t-sql/queries/select-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Per eseguire il comando di **utente del database** tutte queste autorizzazioni o appartenenze deve:  
  
-   **ALTER SCHEMA** autorizzazione per lo schema locale che conterrà la nuova tabella o l'appartenenza di **db_ddladmin** ruolo predefinito del database.  
  
-   **CREATE TABLE** autorizzazione o l'appartenenza di **db_ddladmin** ruolo predefinito del database.  
  
-   **Selezionare** tutti gli oggetti a cui fa riferimento l'autorizzazione per la *select_criteria*.  
  
 L'account di accesso deve tutte queste autorizzazioni:  
  
-   **ADMINISTER BULK OPERATIONS** autorizzazione  
  
-   **ALTER ANY EXTERNAL DATA SOURCE** autorizzazione  
  
-   **ALTER ANY EXTERNAL FILE FORMAT** autorizzazione  
  
-   L'accesso deve disporre dell'autorizzazione di scrittura per leggere e scrivere nella cartella esterna nel Hadoop Cluster o Blob di archiviazione di Azure.  
 
 > [!IMPORTANT]  
 >  L'autorizzazione ALTER ANY EXTERNAL DATA SOURCE concede a qualsiasi entità la possibilità di creare e modificare qualsiasi oggetto di origine dati esterna e di conseguenza, concede inoltre la possibilità di accedere a tutte le credenziali con ambito database nel database. Questa autorizzazione deve essere considerata privilegi elevati e pertanto devono essere concesse solo a entità attendibili nel sistema.
  
## <a name="error-handling"></a>Gestione degli errori  
 Quando CREATE EXTERNAL TABLE AS SELECT Esporta dati in un file delimitato da testo, non si verifica alcun file di rifiuto per le righe che non riescono a esportare.  
  
 Quando si crea la tabella esterna, il database tenta di connettersi al cluster Hadoop esterno o il Blob di archiviazione di Azure. Se la connessione non riesce, il comando avrà esito negativo e non verrà creata la tabella esterna. Può richiedere più di un minuto per il comando di connessione ha esito negativo perché i tentativi di database di almeno 3 volte.  
  
 Se CREATE EXTERNAL TABLE AS SELECT è stata annullata o ha esito negativo, il database verrà effettuata un monouso tentativo di rimuovere tutti i file e cartelle già create nell'origine dati esterna.  
  
 Il database segnalerà gli errori di linguaggio che si verificano sull'origine dati esterna durante l'esportazione di dati.  
  
##  <a name="GeneralRemarks"></a>Osservazioni generali  
 Al termine dell'esecuzione dell'istruzione CETAS, è possibile eseguire [!INCLUDE[tsql](../../includes/tsql-md.md)] query nella tabella esterna. Queste operazioni verranno importati i dati nel database per la durata della query a meno che non si importa utilizzando l'istruzione CREATE TABLE AS SELECT.  
  
 Il nome della tabella esterna e definizione vengono archiviati nei metadati del database. I dati vengono archiviati nell'origine dati esterna.  
  
 I file esterni sono denominati *QueryID_date_time_ID.format*, dove *ID* è un identificatore incrementale e *format* è il formato dei dati esportati. Ad esempio, QID776_20160130_182739_0.orc.  
  
 L'istruzione CETAS sempre creata una tabella non partizionata, anche se la tabella di origine è partizionata.  
  
 Per i piani di query, creata con descrizione, il databaseuses queste operazioni del piano di query per le tabelle esterne:  
  
-   Spostamento casuale esterno  
  
-   Spostare la trasmissione esterna  
  
-   Spostamento di partizione esterno  
  
 **Si applica a:**[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]come prerequisito per la creazione di una tabella esterna, l'amministratore del dispositivo deve configurare la connettività di hadoop.   Per ulteriori informazioni, vedere Configurare la connettività ai dati esterni (Analitica Platform System) nella documentazione di punti di accesso che è possibile scaricare da [qui](http://www.microsoft.com/download/details.aspx?id=48241).  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Poiché i dati della tabella esterna si trovano all'esterno del database, backup e le operazioni di ripristino avrà effetto solo sui dati archiviati nel database. Ciò significa solo i metadati verranno eseguito il backup e ripristino.  
  
 Il database non verifica la connessione all'origine dati esterna quando si ripristina un backup del database che contiene una tabella esterna. Se l'origine originale non è accessibile, il ripristino dei metadati della tabella esterna avrà comunque esito positivo, ma le operazioni di selezione della tabella esterna non riuscirà.  
  
 Il database non garantisce la coerenza dei dati tra databaseand i dati esterni. È, il cliente, responsabile unicamente per mantenere la coerenza tra i dati esterni e il database.  
  
 Operazioni data manipulation language (DML) non sono supportate nelle tabelle esterne. Ad esempio, è possibile usare il [!INCLUDE[tsql](../../includes/tsql-md.md)] aggiornare, inserire o eliminare [!INCLUDE[tsql](../../includes/tsql-md.md)]istruzioni per modificare i dati esterni.  
  
 Istruzione DROP VIEW, CREATE VIEW, DROP STATISTICS, CREATE STATISTICS, DROP TABLE e CREATE TABLE sono le operazioni solo data definition language (DDL) consentite nelle tabelle esterne.  
  
 PolyBase può utilizzare un massimo di file k 33 per ogni cartella durante l'esecuzione di query di PolyBase simultanee 32. Il numero massimo specificato include i file e le sottocartelle in ogni cartella HDFS. Se il livello di concorrenza è minore di 32, un utente può eseguire le query PolyBase sulle cartelle in HDFS che includono più di 33 file k. [!INCLUDE[msCoName](../../includes/msconame-md.md)]gli utenti si consiglia di Hadoop e PolyBase mantenere brevi i percorsi di file e utilizzano non più di 30 file k per ogni cartella HDFS. Quando vengono fatto riferimento troppi file si verifica un'eccezione di esaurimento della memoria JVM.  
  
 [SET ROWCOUNT &#40; Transact-SQL &#41; ](../../t-sql/statements/set-rowcount-transact-sql.md) non ha alcun effetto su questo CREATE EXTERNAL TABLE AS SELECT. Per ottenere un comportamento simile, utilizzare [torna all'inizio &#40; Transact-SQL &#41; ](../../t-sql/queries/top-transact-sql.md).  
  
 Quando si seleziona un RCFile CREATE EXTERNAL TABLE AS SELECT, i valori delle colonne di RCFile non devono contenere la pipe ' |' caratteri.  
  
## <a name="locking"></a>Utilizzo di blocchi  
 Acquisisce un blocco condiviso per l'oggetto SCHEMARESOLUTION.  
  
##  <a name="Examples"></a> Esempi  
  
### <a name="a-create-a-hadoop-table-using-create-external-table-as-select-cetas"></a>A. Creare una tabella di Hadoop utilizzando creare esterno tabella AS selezionare (CETAS)  
 L'esempio seguente crea una nuova tabella esterna denominata `hdfsCustomer`, utilizzando i dati dalla tabella di origine e definizioni di colonna `dimCustomer`.  
  
 La definizione di tabella viene archiviata nel database e i risultati dell'istruzione SELECT vengono esportati per il ' / pdwdata/customer.tbl' file di origine dati esterna Hadoop *customer_ds*. Il file è formattato in base al formato di file esterno *customer_ff*.  
  
 Il nome del file è generato dal database e contiene l'ID di query per facilitare l'allineamento con la query che lo ha generato il file.  
  
 Il percorso `hdfs://xxx.xxx.xxx.xxx:5000/files/` precedente directory del cliente deve essere già esistente. Tuttavia, se non esiste una directory del cliente, il database verrà creare la directory.  
  
> [!NOTE]  
>  In questo esempio specifica per 5000. Se la porta non è specificata, il database utilizza 8020 come porta predefinita.  
  
 La risultante Hadoop percorso e nome file sarà `hdfs:// xxx.xxx.xxx.xxx:5000/files/Customer/ QueryID_YearMonthDay_HourMinutesSeconds_FileIndex.txt.`.  
  
```  
  
      -- Example is based on AdventureWorks   
CREATE EXTERNAL TABLE hdfsCustomer  
WITH (  
        LOCATION='/pdwdata/customer.tbl',  
        DATA_SOURCE = customer_ds,  
        FILE_FORMAT = customer_ff  
) AS SELECT * FROM dimCustomer;  
```  
  
### <a name="b-use-a-query-hint-with-create-external-table-as-select-cetas"></a>B. Utilizzare un Hint per la Query con CREATE EXTERNAL TABLE AS selezionare (CETAS)  
 Questa query Mostra la sintassi di base per l'utilizzo di un hint di join della query con l'istruzione CETAS. Dopo che la query viene inviata il database utilizza la strategia di join hash per generare il piano di query. Per ulteriori informazioni sull'hint di join e come utilizzare la clausola OPTION, vedere [clausola OPTION &#40; Transact-SQL &#41; ](../../t-sql/queries/option-clause-transact-sql.md).  
  
> [!NOTE]  
>  In questo esempio specifica per 5000. Se la porta non è specificata, il database utilizza 8020 come porta predefinita.  
  
```  
  
      -- Example is based on AdventureWorks  
CREATE EXTERNAL TABLE dbo.FactInternetSalesNew  
WITH   
    (   
        LOCATION = '/files/Customer',  
        DATA_SOURCE = customer_ds,  
        FILE_FORMAT = customer_ff  
    )  
AS SELECT T1.* FROM dbo.FactInternetSales T1 JOIN dbo.DimCustomer T2  
ON ( T1.CustomerKey = T2.CustomerKey )  
OPTION ( HASH JOIN );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)   
 [CREATE EXTERNAL FILE FORMAT &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-file-format-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)   
 [CREARE una tabella &#40; Azure SQL Data Warehouse, Parallel Data Warehouse &#41;](~/t-sql/statements/create-table-azure-sql-data-warehouse.md)   
 [CREATE TABLE AS SELECT &#40; Azure SQL Data Warehouse &#41;](../../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md)   
 [DROP TABLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-table-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
  
  



