---
title: "Sottoscrittori non SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sottoscrizioni [replica di SQL Server], Sottoscrittori non SQL Server"
  - "origini di dati eterogenei, Sottoscrittori non SQL Server"
  - "origini dei dati eterogenee"
  - "replica di database eterogenei, Sottoscrittori non SQL Server"
  - "Sottoscrittori non SQL Server, informazioni sui Sottoscrittori non SQL Server"
  - "Sottoscrittori eterogenei"
  - "Sottoscrittori eterogenei, informazioni sui Sottoscrittori eterogenei"
  - "Sottoscrittori [replica di SQL Server], Sottoscrittori non SQL Server"
  - "Sottoscrittori non SQL Server"
ms.assetid: 831e7586-2949-4b9b-a2f3-7b0b699b23ff
caps.latest.revision: 55
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 55
---
# Sottoscrittori non SQL Server
  Tramite i Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] riportati di seguito è possibile eseguire la sottoscrizione di pubblicazioni snapshot e transazionali utilizzando sottoscrizioni push. Le sottoscrizioni sono supportate per le due versioni più recenti di ogni database elencato utilizzando la versione più recente del provider OLE DB elencato.  
  
 La replica eterogenea a Sottoscrittori non SQL Server è deprecata. La pubblicazione Oracle è deprecata. Per spostare dati, creare soluzioni utilizzando Change Data Capture e [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
|Database|Sistema operativo|Provider|  
|--------------|----------------------|--------------|  
|Oracle|Tutte le piattaforme supportate da Oracle|Provider Oracle OLE DB (fornito da Oracle)|  
|IBM DB2|MVS, AS400, Unix, Linux, Windows escluso 9.x|Provider Microsoft Host Integration Server (HIS) OLE DB|  
  
 Per informazioni sulla creazione di sottoscrizioni per Oracle e IBM DB2, vedere [sottoscrittori Oracle](../../../relational-databases/replication/non-sql/oracle-subscribers.md) e [nei Sottoscrittori DB2 IBM](../../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
## Considerazioni sui Sottoscrittori non SQL Server  
 Durante la replica in Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tenere presente quanto segue:  
  
### Considerazioni generali  
  
-   La replica supporta la pubblicazione di tabelle e viste indicizzate come tabelle in Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (le viste indicizzate non possono essere replicate come viste indicizzate).  
  
-   Quando si crea una pubblicazione nella creazione guidata pubblicazione e quindi abilitarlo per sottoscrittori non SQL Server utilizzando la finestra di dialogo Proprietà pubblicazione, il proprietario di tutti gli oggetti nel database di sottoscrizione non è specificato per non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sottoscrittori, mentre per [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sottoscrittori, di impostare il proprietario dell'oggetto corrispondente nel database di pubblicazione.  
  
-   Se una pubblicazione includerà [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sottoscrittori e non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sottoscrittori, nella pubblicazione deve essere abilitato per non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sottoscrittori prima tutte le sottoscrizioni a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono creati i sottoscrittori.  
  
-   Per impostazione predefinita, gli script generati dall'agente snapshot per i Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzano identificatori non racchiusi tra virgolette nella sintassi CREATE TABLE. Pertanto, una tabella pubblicata denominata 'test' viene replicata come 'TEST'. Per utilizzare lo stesso caso della tabella nel database di pubblicazione, utilizzare il **- QuotedIdentifier** parametro dell'agente di distribuzione. Il **- QuotedIdentifier** parametro deve essere utilizzato anche se i nomi di oggetto pubblicato (ad esempio tabelle, colonne e vincoli) includono spazi o parole che sono parole riservate nella versione del database non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sottoscrittore. Per ulteriori informazioni su questo parametro, vedere [agente distribuzione repliche](../../../relational-databases/replication/agents/replication-distribution-agent.md).  
  
-   L'account con il quale viene eseguito l'agente di distribuzione deve disporre di accesso in lettura alla directory di installazione del provider OLE DB.  
  
-   Per impostazione predefinita non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sottoscrittori, l'agente di distribuzione viene utilizzato il valore [(destinazione predefinita)] per il database di sottoscrizione (il **- SubscriberDB** parametro dell'agente di distribuzione):  
  
    -   Per Oracle, un server include al massimo un database e pertanto non è necessario specificare il database.  
  
    -   Per IBM DB2, il database viene specificato nella stringa di connessione DB2. Per ulteriori informazioni, vedere [creare una sottoscrizione per un sottoscrittore Non SQL Server](../../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
-   Se il server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene eseguito su una piattaforma a 64 bit, è necessario utilizzare la versione a 64 bit del provider OLE DB appropriato.  
  
-   La replica consente di spostare i dati in formato Unicode indipendentemente dalla tabella codici e dalle regole di confronto utilizzate nel server di pubblicazione e nel Sottoscrittore. Quando si esegue la replica tra server di pubblicazione e Sottoscrittori è consigliabile scegliere una tabella codici e regole di confronto compatibili.  
  
-   Se un articolo viene aggiunto o eliminato da una pubblicazione, sarà necessario reinizializzare le sottoscrizioni dei Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   I soli vincoli supportati per tutti i Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono NULL e NOT NULL. I vincoli delle chiavi primarie vengono replicati come indici univoci.  
  
-   Il valore NULL viene considerato in modo diverso a seconda del database, con conseguenze sulla modalità di rappresentazione dei valori e delle stringhe vuote e dei valori NULL. Ciò a sua volta influisce sul comportamento dei valori inseriti nelle colonne con vincoli univoci definiti. Oracle consente, ad esempio, più valori NULL in una colonna considerata univoca, mentre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente un solo valore NULL in una colonna univoca.  
  
     Un altro fattore è rappresentato dal modo in cui i valori NULL, le stringhe e i valori vuoti vengono considerati quando la colonna è definita come NOT NULL. Per informazioni sulla risoluzione di questo problema per i sottoscrittori Oracle, vedere [sottoscrittori Oracle](../../../relational-databases/replication/non-sql/oracle-subscribers.md).  
  
-   I metadati correlati alla replica (tabella di sequenza della transazione) non vengono eliminati dai Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quando la sottoscrizione viene rimossa.  
  
### Conformità ai requisiti del database Sottoscrittore  
  
-   Lo schema e i dati pubblicati devono essere conformi ai requisiti del database nel Sottoscrittore. Se, ad esempio, un database non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] presenta una dimensione massima di riga più piccola di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], è necessario accertarsi che lo schema e i dati pubblicati non superino tale dimensione.  
  
-   Le tabelle replicate nei Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] adotteranno le convenzioni di denominazione delle tabelle del database del Sottoscrittore.  
  
-   L'operazione DDL non è supportata per Sottoscrittori non SQL Server. Per ulteriori informazioni sulle modifiche dello schema, vedere [apportare le modifiche dello Schema nei database di pubblicazione](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
### Supporto della funzionalità di replica  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono disponibili due tipi di sottoscrizioni: push e pull. I Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] devono utilizzare le sottoscrizioni push nelle quali l'agente di distribuzione viene eseguito nel server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] offre due formati di snapshot: modalità bcp nativa e in modalità carattere. I Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] richiedono snapshot in modalità carattere.  
  
-   I Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non possono utilizzare le sottoscrizioni ad aggiornamento immediato o ad aggiornamento in coda né possono essere nodi in una topologia peer-to-peer.  
  
-   I Sottoscrittori non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non possono essere inizializzati automaticamente da un backup.  
  
## Vedere anche  
 [Replica di database eterogenei](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Sottoscrizione delle pubblicazioni](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  