---
title: "Impostazione di un sistema di risoluzione dei conflitti dell&#39;articolo di merge | Microsoft Docs"
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
  - "articoli [replica di SQL Server], risoluzione dei conflitti"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
  - "risoluzione dei conflitti di replica di tipo merge [replica di SQL Server], sistemi di risoluzione di articoli di tipo merge"
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Impostazione di un sistema di risoluzione dei conflitti dell&#39;articolo di merge
  In questo argomento viene descritto come specificare un sistema di risoluzione dell'articolo di merge in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
-   **Per specificare un sistema di risoluzione dell'articolo di merge, utilizzando**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   La replica di tipo merge consente i tipi di sistemi di risoluzione dei conflitti dell'articolo indicati di seguito:  
  
    -   Il sistema di risoluzione dei conflitti predefinito. Il comportamento del sistema di risoluzione dei conflitti predefinito dipende dal tipo di sottoscrizione, ovvero se si tratta di una sottoscrizione client o server. Per ulteriori informazioni su come specificare il tipo di sottoscrizione, vedere [specificare un tipo di sottoscrizione di tipo Merge e priorità per la risoluzione dei conflitti & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md).  
  
    -   Un sistema di risoluzione dei conflitti personalizzato, che può essere un gestore della logica di business (scritto in codice gestito) oppure un sistema di risoluzione dei conflitti personalizzato basato su COM. Per altre informazioni, vedere [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md). Se è necessario implementare una logica personalizzata che viene eseguita per ogni riga replicata e non solo per le righe in conflitto, vedere [implementare un gestore della logica di Business per un articolo di Merge](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
    -   Un standard resolver basato su COM, incluso in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Per utilizzare un sistema di risoluzione dei conflitti diverso da quello predefinito, è necessario copiare il sistema desiderato nel computer in cui è in esecuzione l'agente di merge e registrarlo. Se si utilizza un gestore della logica di business, è necessario eseguire la registrazione anche nel server di pubblicazione. L'agente di merge viene eseguito nei sistemi seguenti:  
  
    -   Server di distribuzione per una sottoscrizione push  
  
    -   Sottoscrittore per una sottoscrizione pull  
  
    -   Server [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Internet Information Services (IIS) per una sottoscrizione pull che utilizza la sincronizzazione Web  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Dopo aver registrato il sistema di risoluzione, specificare che un articolo deve usare il resolver di **Resolver** scheda del **Proprietà articolo - \< articolo>** la finestra di dialogo, disponibile nella creazione guidata pubblicazione e il **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'utilizzo della procedura guidata e l'accesso nella finestra di dialogo, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per specificare un sistema di risoluzione dei conflitti  
  
1.  Nel **articoli** pagina della procedura guidata nuova pubblicazione o **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare una tabella.  
  
2.  Fare clic su **Proprietà articolo**e quindi su **Imposta proprietà dell'articolo di tabella evidenziato**.  
  
3.  Nel **Proprietà articolo - \< articolo>** pagina, fare clic sui **Resolver** scheda.  
  
4.  Selezionare **utilizzare un resolver personalizzato (registrato nel server di distribuzione)**, quindi nell'elenco, scegliere il sistema di risoluzione.  
  
5.  Se il sistema di risoluzione richiede input (ad esempio un nome di colonna), specificarlo nella **Immettere le informazioni necessarie da parte del resolver** casella di testo.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  Ripetere questa procedura per ogni articolo che richiede un sistema di risoluzione dei conflitti.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per registrare un sistema di risoluzione dei conflitti personalizzato  
  
1.  Se si intende registrare un sistema di risoluzione dei conflitti personalizzato, creare uno dei tipi seguenti:  
  
    -   Sistema di risoluzione basato su codice gestito come gestore della logica di business. Per altre informazioni, vedere [Implement a Business Logic Handler for a Merge Article](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
    -   Sistema di risoluzione basato sulla stored procedure e sistema di risoluzione basato su COM. Per altre informazioni, vedere [Implement a Custom Conflict Resolver for a Merge Article](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md).  
  
2.  Per determinare se il sistema di risoluzione desiderato è già registrato, eseguire [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) nel server di pubblicazione in qualsiasi database. Verrà visualizzata una descrizione del sistema di risoluzione personalizzato, nonché l'identificatore di classe (CLSID) di ogni sistema di risoluzione basato su COM registrato nel server di distribuzione oppure informazioni sull'assembly gestito per ogni gestore della logica di business registrato nel server di distribuzione.  
  
3.  Se il sistema di risoluzione personalizzato desiderato non è già registrato, eseguire [sp_registercustomresolver & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md) nel server di distribuzione. Specificare un nome per il resolver per **@article_resolver**; per un gestore della logica di business, questo è il nome descrittivo dell'assembly. Per i resolver basato su COM, specificare il CLSID della DLL di **@resolver_clsid**, e per un gestore della logica di business, specificare un valore di **true** per **@is_dotnet_assembly**, il nome dell'assembly per **@dotnet_assembly_name**, e il nome completo della classe che esegue l'override <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> per **@dotnet_class_name**.  
  
    > [!NOTE]  
    >  Se un assembly gestore della logica di business non viene distribuito nella stessa directory dell'eseguibile dell'agente di Merge, nella stessa directory dell'applicazione che avvia in modo sincrono l'agente di Merge o nella global assembly cache (GAC), è necessario specificare il percorso completo con il nome dell'assembly per **@dotnet_assembly_name**.  
  
4.  Se il sistema di risoluzione è basato su COM:  
  
    -   Copiare la DLL del sistema di risoluzione personalizzato nel server di distribuzione per le sottoscrizioni push o nel Sottoscrittore per le sottoscrizioni pull.  
  
        > [!NOTE]  
        >  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] sistemi di risoluzione personalizzati, vedere il [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]directory COM.  
  
    -   Utilizzare regsvr32.exe per registrare la DLL del sistema di risoluzione personalizzato con il sistema operativo. Ad esempio, eseguire il seguente comando dal prompt dei comandi per registrare il sistema di risoluzione dei conflitti aggiuntivi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  Se il sistema di risoluzione è un gestore della logica di business, distribuire l'assembly nella stessa cartella dell'eseguibile dell'agente di Merge (replmerg.exe), nella stessa cartella di un'applicazione che richiama l'agente di Merge o nella cartella specificata per il **@dotnet_assembly_name** parametro nel passaggio 3.  
  
    > [!NOTE]  
    >  Il percorso di installazione predefinito del file eseguibile dell'agente di merge è [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.  
  
#### Per specificare un sistema di risoluzione personalizzato durante la definizione di un articolo di merge  
  
1.  Se si intende utilizzare un sistema di risoluzione dei conflitti personalizzato, crearlo e registrarlo utilizzando la procedura sopra riportata.  
  
2.  Server di pubblicazione, eseguire [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) prendere nota del nome del sistema di risoluzione personalizzato desiderato nel **valore** campo del set di risultati.  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare il nome del sistema di risoluzione ottenuto al passaggio 2 per **@article_resolver** e l'eventuale input obbligatorio per il sistema di risoluzione personalizzato utilizzando il **@resolver_info** parametro. Per la stored procedure basate sistemi di risoluzione personalizzati, **@resolver_info** è il nome della stored procedure. Per ulteriori informazioni sull'input obbligatorio per i resolver forniti da [!INCLUDE[msCoName](../../../includes/msconame-md.md)], vedere [Microsoft sistemi di risoluzione basati su COM](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
#### Per specificare o modificare un sistema di risoluzione personalizzato per un articolo di merge esistente  
  
1.  Per determinare se è stato definito un resolver personalizzato per un articolo o per ottenere il nome del sistema di risoluzione, eseguire [sp_helpmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Se è presente un resolver personalizzato definito per l'articolo, il relativo nome verrà visualizzato nel **article_resolver** campo. Verrà visualizzata qualsiasi input fornito al sistema di risoluzione di **resolver_info** campo del set di risultati.  
  
2.  Server di pubblicazione, eseguire [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) prendere nota del nome del sistema di risoluzione personalizzato desiderato nel **valore** campo del set di risultati.  
  
3.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare un valore di **article_resolver**, incluso il percorso completo per gestori della logica di business, per **@property**, e il nome del sistema di risoluzione personalizzato desiderato ottenuto al passaggio 2 per **@value**.  
  
4.  Per modificare eventuale input obbligatorio per il resolver personalizzato, eseguire [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) di nuovo. Specificare un valore di **resolver_info** per **@property** e l'eventuale input obbligatorio per il sistema di risoluzione personalizzato per **@value**. Per la stored procedure basate sistemi di risoluzione personalizzati, **@resolver_info** è il nome della stored procedure. Per ulteriori informazioni sull'input obbligatorio, vedere [Microsoft sistemi di risoluzione basati su COM](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
#### Per annullare la registrazione di un sistema di risoluzione dei conflitti personalizzato  
  
1.  Server di pubblicazione, eseguire [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) prendere nota del nome di sistema di risoluzione personalizzato per rimuovere il **valore** campo del set di risultati.  
  
2.  Eseguire [sp_unregistercustomresolver & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md) nel server di distribuzione. Specificare il nome completo del sistema di risoluzione personalizzato ottenuto al passaggio 1 per **@article_resolver**.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 In questo esempio viene creato un nuovo articolo e viene impostato l'utilizzo del sistema di risoluzione dei conflitti medi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per calcolare la media della colonna **UnitPrice** in caso di conflitti.  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../relational-databases/replication/codesnippet/tsql/specify-a-merge-article-_1.sql)]  
  
 In questo esempio un articolo viene impostato in modo da utilizzare il sistema di risoluzione dei conflitti aggiuntivi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per calcolare la somma della colonna **UnitsOnOrder** in caso di conflitti.  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../relational-databases/replication/codesnippet/tsql/specify-a-merge-article-_2.sql)]  
  
## Vedere anche  
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Implementazione di un gestore della logica di business per un articolo di merge](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
  