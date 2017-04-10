---
title: "Gestione delle colonne Identity | Microsoft Docs"
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
  - "valori Identity [replica di SQL Server]"
  - "replica di tipo merge [replica di SQL Server], gestione degli intervalli di valori Identity"
  - "pubblicazione [replica di SQL Server], colonne Identity"
  - "replica transazionale, gestione degli intervalli di valori Identity"
  - "colonne Identity [SQL Server], replica"
ms.assetid: 98892836-cf63-494a-bd5d-6577d9810ddf
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 42
---
# Gestione delle colonne Identity
  In questo argomento viene descritto come gestire le colonne Identity in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Quando gli inserimenti del Sottoscrittore vengono replicati nel server di pubblicazione, è necessario gestire le colonne Identity in modo da evitare l'assegnazione dello stesso valore Identity sia al Sottoscrittore che al server di pubblicazione. È possibile gestire automaticamente intervalli di valori Identity tramite la replica oppure scegliere di gestirli manualmente.  Per informazioni sulle opzioni di gestione intervallo identity fornite dalla replica, vedere [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
-   **Per gestire le colonne Identity, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Quando si pubblica una tabella in più di una pubblicazione, è necessario specificare le stesse opzioni di gestione degli intervalli di valori Identity per entrambi le pubblicazioni. Per ulteriori informazioni, vedere "Pubblicazione le tabelle in più pubblicazioni" in [pubblicare dati e oggetti di Database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md).  
  
-   Per creare un numero a incremento automatico che può essere utilizzato in più tabelle o che può essere chiamato dalle applicazioni senza fare riferimento a qualsiasi tabella, vedere [numeri di sequenza](../../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Specificare un'opzione di gestione di colonne identity nel **proprietà** scheda della finestra di **Proprietà articolo - \< articolo>** la finestra di dialogo della procedura guidata nuova pubblicazione. Per ulteriori informazioni sull'utilizzo di questa procedura guidata, vedere [creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md). Nella Creazione guidata nuova pubblicazione:  
  
-   Se si seleziona **pubblicazione di tipo Merge** o **pubblicazione transazionale con sottoscrizioni aggiornabili** sul **tipo di pubblicazione** selezionare Gestione intervalli di valori identity automatico o manuale (automatico, il valore predefinito, è consigliato). Dopo la pubblicazione della tabella la proprietà non può più essere modificata, mentre è possibile modificare altre proprietà correlate.  
  
-   Se si selezionano altri tipi di pubblicazioni, è necessario impostare la gestione degli intervalli di valori Identity su manuale.  
  
 Modificare le soglie e intervalli di valori identity nel **proprietà** scheda della finestra di **Proprietà articolo - \< articolo>**, disponibile nel **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Per specificare un'opzione per la gestione di colonne Identity  
  
1.  Se il server di pubblicazione è in esecuzione una versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prima di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], via il **tipo di pubblicazione** pagina della creazione guidata pubblicazione, selezionare **pubblicazione di tipo Merge** o **pubblicazione transazionale con sottoscrizioni aggiornabili**.  
  
2.  Nel **articoli** pagina, selezionare una tabella con una colonna identity.  
  
3.  Fare clic su **Proprietà articolo**e quindi su **Imposta proprietà dell'articolo di tabella evidenziato**.  
  
4.  Nel **proprietà** scheda del **Proprietà articolo - \< articolo>** della finestra di dialogo di **Gestione intervalli di valori Identity** sezione, impostare il **gestire automaticamente intervalli di valori identity** proprietà **automatica** o **manuale** (di pubblicazione che eseguono [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva), o **True** o **False** (di pubblicazione che eseguono una versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prima di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]).  
  
5.  Se si seleziona **automatica** o **True** nel passaggio 4, immettere i valori per le opzioni nella tabella seguente. Per ulteriori informazioni sull'utilizzo di queste impostazioni, vedere la sezione "Assegnazione di intervalli di valori Identity" di [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
    |Opzione|Valore|Descrizione|  
    |------------|-----------|-----------------|  
    |**Dimensioni intervallo server di pubblicazione**|Valore intero per le dimensioni dell'intervallo, ad esempio 20000.|Vedere la sezione "Assegnazione di intervalli di valori Identity" di [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).|  
    |**Dimensioni intervallo Sottoscrittore**|Valore intero per le dimensioni dell'intervallo, ad esempio 10000.|Vedere la sezione "Assegnazione di intervalli di valori Identity" di [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).|  
    |**Percentuale soglia intervallo**|Valore intero percentuale per la soglia dell'intervallo, ad esempio 90 è equivalente a 90%.|Percentuale dei valori Identity totali utilizzati in corrispondenza di un nodo prima dell'assegnazione di un nuovo intervallo di valori Identity.<br /><br /> <br /><br /> Nota: Questo valore deve essere specificato, ma viene utilizzato solo da: i sottoscrittori che utilizzano l'aggiornamento di sottoscrizioni in coda i sottoscrittori che eseguono pubblicazioni di tipo merge e [!INCLUDE[ssEW](../../../includes/ssew-md.md)] o versioni precedenti di altre edizioni di SQL Server. Per ulteriori informazioni, vedere la sezione "Assegnazione di intervalli di valori Identity" di [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).|  
    |**Valore iniziale intervallo successivo**|Valore intero. Di sola lettura.|Il valore in corrispondenza del quale inizierà l'intervallo successivo. Ad esempio, se l'intervallo corrente è 5001-6000, questo valore sarà 6001.|  
    |**Valore Identity massimo**|Valore intero. Di sola lettura.|Il valore maggiore per la colonna Identity. Determinato dal tipo di dati di base della colonna.|  
    |**Incremento valore Identity**|Valore intero. Di sola lettura.|La quantità in base alla quale il numero nella colonna Identity deve aumentare o diminuire per ciascun inserimento: in genere è impostata su 1.|  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per modificare le soglie e gli intervalli di valori Identity dopo la pubblicazione di una tabella  
  
1.  Nel **articoli** pagina della **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo, selezionare una tabella con una colonna identity.  
  
2.  Fare clic su **Proprietà articolo**e quindi su **Imposta proprietà dell'articolo di tabella evidenziato**.  
  
3.  Nel **proprietà** scheda del **Proprietà articolo - \< articolo>** della finestra di dialogo di **Gestione intervalli di valori Identity** sezione, immettere i valori per uno o più delle seguenti proprietà: **Dimensioni intervallo server di pubblicazione**, **Dimensioni intervallo Sottoscrittore**, e **Percentuale soglia intervallo**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Fare clic su **OK** sulla **Proprietà pubblicazione - \< pubblicazione>** la finestra di dialogo.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile utilizzare stored procedure di replica per specificare le opzioni di gestione degli intervalli di valori Identity durante la creazione di un articolo.  
  
#### Per abilitare la gestione automatica degli intervalli di valori Identity durante la definizione di articoli per una pubblicazione transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Se la tabella di origine da pubblicare include una colonna identity, specificare un valore di **automatica** per **@identityrangemanagementoption**, l'intervallo di valori identity assegnato al server di pubblicazione per **@pub_identity_range**, l'intervallo di valori identity assegnato a ogni server di sottoscrizione per **@identity_range**, e la percentuale di valori identity totali utilizzati prima dell'assegnazione di un nuovo intervallo di valori identity per **@threshold**. Per ulteriori informazioni sulla definizione degli articoli, vedere [definire un articolo](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Assicurarsi che il tipo di dati della colonna Identity sia sufficiente per supportare l'intervallo totale di valori Identity da assegnare a tutti i Sottoscrittori.  
  
#### Per disabilitare la gestione automatica degli intervalli di valori Identity durante la definizione di articoli per una pubblicazione transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Specificare un valore di **manuali** per **@identityrangemanagementoption**. Per ulteriori informazioni sulla definizione degli articoli, vedere [definire un articolo](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Assegnare intervalli a colonne Identity dell'articolo nel Sottoscrittore per evitare di generare conflitti durante l'aggiornamento dei Sottoscrittori. Per ulteriori informazioni, vedere la sezione sull'assegnazione di intervalli per la gestione manuale nell'argomento [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
#### Per attivare la gestione automatica degli intervalli di valori Identity durante la definizione di articoli per una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Se la tabella di origine da pubblicare include una colonna identity, specificare un valore di **automatica** per **@identityrangemanagementoption**, l'intervallo di valori identity assegnato a una sottoscrizione server per **@pub_identity_range**, l'intervallo di valori identity assegnato al server di pubblicazione e ogni sottoscrizione client per **@identity_range**, e la percentuale di valori identity totali utilizzati prima dell'assegnazione di un nuovo intervallo di valori identity per **@threshold**. Per ulteriori informazioni su quando vengono assegnati nuovi intervalli di valori identity, vedere assegnazione di intervalli di valori Identity nell'argomento [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md). Per ulteriori informazioni sulla definizione degli articoli, vedere [definire un articolo](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Assicurarsi che il tipo di dati della colonna Identity sia sufficiente per supportare l'intervallo totale di valori Identity da assegnare a tutti i Sottoscrittori, in particolare ai Sottoscrittori con sottoscrizioni server.  
  
#### Per disabilitare la gestione automatica degli intervalli di valori Identity durante la definizione di articoli per una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare uno dei valori seguenti per **@identityrangemanagementoption**:  
  
    -   **manuale** -intervalli di valori Identity devono essere assegnati manualmente per l'aggiornamento dei sottoscrittori.  
  
    -   **Nessuno** -le colonne Identity nel server di pubblicazione non verranno definite come colonne identity nel Sottoscrittore.  
  
     Per ulteriori informazioni sulla definizione degli articoli, vedere [definire un articolo](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Assegnare intervalli a colonne Identity dell'articolo nel Sottoscrittore per evitare di generare conflitti durante l'aggiornamento dei Sottoscrittori.  
  
#### Per modificare le impostazioni relative alla gestione automatica degli intervalli di valori Identity per un articolo esistente di una pubblicazione snapshot o transazionale  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md) e prendere nota del valore di **identityrangemanagementoption** nel set di risultati. Se questo valore è **0**, gestione di intervalli di valori identity automatico non è abilitata.  
  
2.  Se il valore di **identityrangemanagementoption** nel set di risultati è **1**, modificare le impostazioni come segue:  
  
    -   Per modificare gli intervalli identity assegnati, eseguire [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **identity_range** o **pub_identity_range** per **@property** e il nuovo valore di intervallo per **@value**.  
  
    -   Per modificare la soglia in cui vengono assegnati nuovi intervalli, eseguire [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **soglia** per **@property** e il nuovo valore di soglia per **@value**.  
  
#### Per modificare le impostazioni relative alla gestione automatica degli intervalli di valori Identity per un articolo esistente di una pubblicazione di tipo merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) e prendere nota del valore di **identity_support** nel set di risultati. Se questo valore è **0**, gestione di intervalli di valori identity automatico non è abilitata.  
  
2.  Se il valore di **identity_support** nel set di risultati è **1**, modificare le impostazioni come segue:  
  
    -   Per modificare gli intervalli identity assegnati, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **identity_range** o **pub_identity_range** per **@property** e il nuovo valore di intervallo per **@value**.  
  
    -   Per modificare la soglia in cui vengono assegnati nuovi intervalli, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **soglia** per **@property** e il nuovo valore di soglia per **@value**. Per ulteriori informazioni su quando vengono assegnati nuovi intervalli di valori identity, vedere assegnazione di intervalli di valori Identity nell'argomento [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
    -   Per disabilitare la gestione di intervalli di valori identity automatici, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **identityrangemanagementoption** per **@property** e **manuale** o **Nessuno** per **@value**.  
  
## Vedere anche  
 [Replica transazionale peer-to-peer](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Replica di colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  