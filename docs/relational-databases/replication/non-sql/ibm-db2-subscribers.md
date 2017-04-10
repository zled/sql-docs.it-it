---
title: "Sottoscrittori IBM DB2 | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sottoscrittori non SQL Server, IBM DB2"
  - "tipi di dati [replica di SQL Server], Sottoscrittori non SQL Server"
  - "Sottoscrittori IBM DB2"
  - "mapping di tipi di dati [replica di SQL Server]"
  - "Sottoscrittori eterogenei, IBM DB2"
ms.assetid: a1a27b1e-45dd-4d7d-b6c0-2b608ed175f6
caps.latest.revision: 74
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 73
---
# Sottoscrittori IBM DB2
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta le sottoscrizioni push a IBM DB2/AS 400, DB2/MVS e DB2/Universal Database tramite i provider OLE DB sono inclusi con [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host Integration Server.  
  
## Configurazione di un Sottoscrittore IBM DB2  
 Per configurare un Sottoscrittore IBM DB2, eseguire la procedura seguente:  
  
1.  Installare la versione più recente del provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB per DB2 nel server di distribuzione:  
  
    -   Se si utilizza [!INCLUDE[ssEnterpriseEd11](../../../includes/ssenterpriseed11-md.md)], nella pagina Web [Download di SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=149256) fare clic sul collegamento alla versione più recente del Feature Pack di Microsoft SQL Server 2008 nella sezione **Download correlati** . Nella pagina Web **Feature Pack di Microsoft SQL Server 2008** cercare **Provider Microsoft OLE DB per DB2**.  
  
    -   Se si utilizza [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Standard, installare la versione più recente del server [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Host [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] (HIS), che include il provider.  
  
     Oltre a installare il provider, si consiglia di installare lo strumento di accesso ai dati, viene utilizzato nel passaggio successivo (è installato per impostazione predefinita con il download per [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Enterprise). Per ulteriori informazioni sull'installazione e sull'utilizzo dello strumento di accesso ai dati, vedere la documentazione del provider o di HIS.  
  
2.  Creare una stringa di connessione per il Sottoscrittore. La stringa di connessione può essere creata in qualsiasi editor di testo, ma è consigliabile utilizzare lo strumento di accesso ai dati. Per creare la stringa nello strumento di accesso ai dati:  
  
    1.  Fare clic sul menu **Start**, scegliere **Programmi**, **Provider Microsoft OLE DB per DB2**e quindi **Strumento di accesso ai dati**.  
  
    2.  In **Strumento di accesso ai dati**eseguire la procedura per fornire informazioni sul server DB2. Al termine della procedura, verrà creato un collegamento dati universale (UDL) con una stringa di connessione associata. Sarà tale stringa a essere utilizzata dalla replica e non il collegamento UDL.  
  
    3.  Accedere alla stringa di connessione: fare doppio clic sul collegamento UDL nello strumento di accesso ai dati e selezionare **Visualizza stringa di connessione**.  
  
     La stringa di connessione sarà simile alla seguente (le interruzioni di linea sono state inserite per favorire la leggibilità):  
  
    ```  
    Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
    PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
    Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
    Persist Security Info=False;Connection Pooling=True;  
    ```  
  
     La maggior parte delle opzioni nella stringa è specifica per il server DB2 configurato, ma è necessario che l'opzione `Process Binary as Character` sia sempre impostata su `False`. È necessario specificare un valore per l'opzione `Initial Catalog` per identificare il database di sottoscrizione. La stringa di connessione verrà immessa nella Creazione guidata nuova sottoscrizione durante la creazione della sottoscrizione.  
  
3.  Creare uno snapshot o una pubblicazione transazionale, abilitarlo per i Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], quindi creare una sottoscrizione push per il Sottoscrittore. Per ulteriori informazioni, vedere [creare una sottoscrizione per un sottoscrittore Non SQL Server](../../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
4.  Se necessario, specificare uno script di creazione personalizzato per uno o più articoli. Quando viene pubblicata una tabella, viene creato uno script CREATE TABLE per la tabella. Per i Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lo script viene creato nel sottolinguaggio [!INCLUDE[tsql](../../../includes/tsql-md.md)] e viene quindi convertito in un sottolinguaggio SQL più generico dall'agente di distribuzione prima di essere applicato al Sottoscrittore. Per specificare uno script di creazione personalizzato, modificare esistente [!INCLUDE[tsql](../../../includes/tsql-md.md)] script o creare uno script completo che utilizza il sottolinguaggio DB2 SQL; se viene creato uno script DB2, utilizzare il **bypass_translation** direttiva in modo che l'agente di distribuzione possa applicare lo script nel Sottoscrittore senza conversione.  
  
     Gli script possono essere modificati per numerosi motivi, ma quello più comune consiste nella necessità di modificare i mapping dei tipi di dati. Per ulteriori informazioni, vedere la sezione "Considerazioni sui mapping dei tipi di dati" di seguito in questo argomento. Se si modifica lo script [!INCLUDE[tsql](../../../includes/tsql-md.md)], è consigliabile limitare le modifiche solo ai mapping dei tipi di dati. Lo script non dovrà inoltre contenere commenti. Se sono necessarie modifiche più sostanziali, creare uno script DB2.  
  
     **Per modificare lo script di un articolo e fornirlo come script di creazione personalizzato**  
  
    1.  Dopo avere generato uno snapshot per la pubblicazione, passare alla cartella snapshot per la pubblicazione.  
  
    2.  Individuare il file sch che ha lo stesso nome dell'articolo, ad esempio MyArticle.sch.  
  
    3.  Aprire il file utilizzando il Blocco note o un altro editor di testo.  
  
    4.  Modificare il file e salvarlo in una directory diversa.  
  
    5.  Eseguire sp_changearticle, specificando il percorso e nome per il *creation_script* proprietà. Per ulteriori informazioni, vedere [sp_changearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md).  
  
     **Per creare lo script di un articolo e fornirlo come script di creazione personalizzato**  
  
    1.  Creare lo script di un articolo utilizzando il sottolinguaggio DB2 SQL. Verificare che sia la prima riga del file **bypass_translation**, con esclusivamente sulla riga.  
  
    2.  Eseguire sp_changearticle, specificando il percorso e nome per il *creation_script* proprietà.  
  
## Considerazioni per i Sottoscrittori IBM DB2  
 Oltre alle considerazioni descritte nell'argomento [sottoscrittori Non SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md), prendere in considerazione i seguenti problemi durante la replica nei Sottoscrittori DB2:  
  
-   I dati e gli indici per ogni tabella replicata sono associati a un spazio tabella DB2. La dimensione della pagina di uno spazio tabella DB2 controlla il numero massimo di colonne e la dimensione massima delle righe delle tabelle che appartengono allo spazio tabella. Verificare che lo spazio tabella associato alle tabelle replicate sia appropriato al numero di colonne replicate e alla dimensione massima delle righe delle tabelle.  
  
-   Non pubblicare tabelle nei Sottoscrittori DB2 utilizzando una replica transazionale se i dati di una o più colonne chiave primaria nella tabella sono di tipo DECIMAL(32-38, 0-38) o NUMERIC(32-38, 0-38). La replica transazionale identifica le righe utilizzando la chiave primaria. Ciò può dar luogo a errori, in quanto per i tipi di dati viene eseguito il mapping a VARCHAR(41) nel Sottoscrittore. Le tabelle con chiavi primarie che utilizzano questi tipi di dati possono essere pubblicate tramite la replica snapshot.  
  
-   Se si desidera creare tabelle nel Sottoscrittore evitando che vengano create dalla replica, utilizzare l'opzione replication support only. Per ulteriori informazioni, vedere [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono consentiti nomi di tabella e nomi di colonna più lunghi rispetto a DB2:  
  
    -   Se il database di pubblicazione include tabelle con nomi più lunghi di quelli supportati nella versione DB2 del Sottoscrittore, specificare un nome alternativo per la proprietà dell'articolo destination_table. Per ulteriori informazioni sull'impostazione delle proprietà quando si crea una pubblicazione, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [definire un articolo](../../../relational-databases/replication/publish/define-an-article.md).  
  
    -   Non è possibile specificare nomi di colonna alternativi. È necessario verificare che le tabelle pubblicate non includano nomi di colonna più lunghi di quelli supportati nella versione DB2 del Sottoscrittore.  
  
## Mapping dei tipi di dati tra SQL Server e IBM DB2  
 Nella tabella seguente vengono illustrati i mapping dei tipi di dati utilizzati quando si esegue la replica dei dati in un Sottoscrittore in cui è in esecuzione IBM DB2.  
  
|Tipo di dati di SQL Server|Tipo di dati IBM DB2|  
|--------------------------|-----------------------|  
|**bigint**|DECIMAL(19,0)|  
|**Binary(1-254)**|CHAR(1-254) FOR BIT DATA|  
|**Binary(255-8000)**|VARCHAR(255-8000) FOR BIT DATA|  
|**bit**|SMALLINT|  
|**Char(1-254)**|CHAR(1-254)|  
|**Char(255-8000)**|VARCHAR(255-8000)|  
|**data**|DATE|  
|**datetime**|TIMESTAMP|  
|**datetime2(0-7)**|VARCHAR(27)|  
|**DateTimeOffset(0-7)**|VARCHAR(34)|  
|**Decimal (1-31, 0-31)**|DECIMAL(1-31, 0-31)|  
|**Decimal (32-38, 0-38)**|VARCHAR(41)|  
|**float(53)**|DOUBLE|  
|**FLOAT**|FLOAT|  
|**geography**|IMAGE|  
|**geometry**|IMAGE|  
|**hierarchyid**|IMAGE|  
|**image**|VARCHAR(0) FOR BIT DATA*|  
|**into**|INT|  
|**money**|DECIMAL(19,4)|  
|**nchar(1-4000)**|VARCHAR(1-4000)|  
|**ntext**|VARCHAR(0) *|  
|**numeriche (1-31, 0-31)**|DECIMAL(1-31,0-31)|  
|**numerico (32-38, 0-38)**|VARCHAR(41)|  
|**nvarchar(1-4000)**|VARCHAR(1-4000)|  
|**nvarchar(max)**|VARCHAR(0) *|  
|**real**|REAL|  
|**smalldatetime**|TIMESTAMP|  
|**SMALLINT**|SMALLINT|  
|**smallmoney**|DECIMAL(10,4)|  
|**sql_variant**|N/D|  
|**sysname**|VARCHAR(128)|  
|**text**|VARCHAR(0) *|  
|**Time(0-7)**|VARCHAR(16)|  
|**timestamp**|CHAR(8) FOR BIT DATA|  
|**tinyint**|SMALLINT|  
|**uniqueidentifier**|CHAR(38)|  
|**varbinary(1-8000)**|VARCHAR(1-8000) FOR BIT DATA|  
|**varchar(1-8000)**|VARCHAR(1-8000)|  
|**varbinary(max)**|VARCHAR(0) FOR BIT DATA*|  
|**varchar(max)**|VARCHAR(0) *|  
|**xml**|VARCHAR(0) *|  
  
 *Vedere la sezione successiva per altre informazioni sui mapping al tipo di dati VARCHAR(0).  
  
### Considerazioni sui mapping dei tipi di dati  
 Quando si esegue la replica nei Sottoscrittori DB2, considerare gli aspetti seguenti relativi ai mapping dei tipi di dati:  
  
-   Durante il mapping di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char**, **varchar**, **binario** e **varbinary** DB2 CHAR, VARCHAR, CHAR FOR BIT DATA e VARCHAR FOR BIT DATA, rispettivamente, la replica imposta la lunghezza del tipo di dati DB2 affinché corrisponda a quello del [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo.  
  
     In questo modo, la tabella generata viene creata correttamente nel Sottoscrittore, a condizione che il vincolo relativo alla dimensione della pagina DB2 consenta di supportare la dimensione massima delle righe. Verificare che l'account di accesso al database DB2 disponga delle autorizzazioni per utilizzare gli spazi tabella con dimensioni sufficienti per le tabelle replicate in DB2.  
  
-   DB2 può supportare colonne VARCHAR di grandezza pari a 32 KB. È pertanto possibile che venga eseguito correttamente il mapping tra alcune colonne LOB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e le colonne VARCHAR DB2. Il provider OLE DB utilizzato dalla replica per DB2, tuttavia, non supporta l'esecuzione del mapping tra oggetti di grandi dimensioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e oggetti di grandi dimensioni di DB2. Per questo motivo, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **testo**, **varchar (max)**, **ntext**, e **nvarchar (max)** colonne sono mappate a VARCHAR(0) negli script di creazione generati. È necessario modificare il valore di lunghezza 0 in un valore appropriato prima di applicare lo script nel Sottoscrittore. Se la lunghezza del tipo di dati non cambia, in DB2 viene generato l'errore 604 quando si tenta di creare la tabella nel Sottoscrittore DB2. L'errore 604 indica che l'attributo di precisione o di lunghezza di un tipo di dati non è valido.  
  
     In base alle informazioni in proprio possesso sulla tabella di origine di cui si esegue la replica, determinare se sia opportuno eseguire il mapping tra un oggetto di grandi dimensioni di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e un elemento DB2 di lunghezza variabile e specificare una lunghezza massima appropriata in uno script di creazione personalizzato. Per informazioni sulla definizione di uno script di creazione personalizzato, vedere il passaggio 5 nella sezione "Configurazione di un Sottoscrittore IBM DB2" in questo argomento.  
  
    > [!NOTE]  
    >  La lunghezza specificata per il tipo DB2, se associata ad altre lunghezze di colonna, non può superare la dimensione massima delle righe basata sullo spazio tabella DB2 cui sono assegnati i dati della tabella.  
  
     Se non esiste alcun mapping appropriato per una colonna LOB, valutare l'opportunità di applicare filtri colonne nell'articolo affinché la colonna non venga replicata. Per ulteriori informazioni, vedere [filtrare i dati pubblicati](../../../relational-databases/replication/publish/filter-published-data.md).  
  
-   Quando si replicano [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **nchar** e **nvarchar** DB2 CHAR e VARCHAR, la replica utilizza lo stesso identificatore di lunghezza per il tipo DB2 che per il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipo. La lunghezza del tipo di dati, tuttavia, potrebbe essere troppo ridotta per la tabella DB2 generata.  
  
     In alcuni ambienti DB2 un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char** elemento di dati non è limitato a caratteri a byte singolo, la lunghezza di un elemento di tipo CHAR o VARCHAR necessario prendere in considerazione. È inoltre necessario considerare i *caratteri di controllo SI* e i *caratteri di controllo SO* , se richiesti. Se si replicano tabelle con colonne **nchar** e **nvarchar** , potrebbe essere necessario specificare una lunghezza massima maggiore per il tipo di dati in uno script di creazione personalizzato. Per informazioni sulla definizione di uno script di creazione personalizzato, vedere il passaggio 5 nella sezione "Configurazione di un Sottoscrittore IBM DB2" in questo argomento.  
  
## Vedere anche  
 [Sottoscrittori non SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Sottoscrizione delle pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  