---
title: "Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge | Microsoft Docs"
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
  - "risoluzione dei conflitti di replica di tipo merge [replica di SQL Server], informazioni sulla risoluzione dei conflitti"
  - "sistema di risoluzione di conflitti predefinito"
  - "registrazione di conflitti a livello di colonna"
  - "registrazione di conflitti a livello di riga"
  - "visualizzazione di conflitti di replica di tipo merge"
  - "risoluzione di conflitti di replica di tipo merge"
  - "registrazione logica di conflitti a livello di record [replica di SQL Server]"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
ms.assetid: 063d3d9c-ccb5-4fab-9d0c-c675997428b4
caps.latest.revision: 46
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 46
---
# Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge
  Se un server di pubblicazione e un Sottoscrittore sono connessi e viene eseguita la sincronizzazione, l'agente di merge rileva l'eventuale presenza di conflitti. Se vengono rilevati dei conflitti, l'agente utilizza un sistema di risoluzione dei conflitti, specificato al momento dell'aggiunta di un articolo a una pubblicazione, per determinare quali dati vengono accettati e propagati agli altri siti.  
  
> [!NOTE]  
>  Sebbene un Sottoscrittore esegua la sincronizzazione con il server di pubblicazione, i conflitti in genere si verificano tra gli aggiornamenti effettuati in diversi Sottoscrittori anziché tra gli aggiornamenti effettuati in un Sottoscrittore e nel server di pubblicazione.  
  
 La procedura di rilevamento e risoluzione dei conflitti dipende dalle opzioni seguenti, descritte in questo argomento:  
  
-   Se si specifica il rilevamento a livello di colonna, a livello di riga o a livello di record logico.  
  
-   Se si specifica il meccanismo predefinito di risoluzione basato sulla priorità o un sistema di risoluzione dei conflitti dell'articolo. Il sistema di risoluzione dei conflitti dell'articolo può essere costituito da:  
  
    -   Oggetto *gestore della logica di business* scritti in codice gestito.  
  
    -   Basato su COM *resolver personalizzato*.  
  
    -   Un sistema di risoluzione basato sul modello COM implementato da [!INCLUDE[msCoName](../../../includes/msconame-md.md)].  
  
     Se si utilizza il meccanismo di risoluzione predefinito, la procedura è determinata inoltre dal tipo di sottoscrizione selezionato: client o server.  
  
## Rilevamento dei conflitti  
 Una modifica dei dati viene considerata o meno un conflitto in base al tipo di rilevamento dei conflitti impostato per un articolo:  
  
-   Se si seleziona il rilevamento dei conflitti a livello di colonna, le modifiche vengono considerate in conflitto se vengono apportate alla stessa colonna e alla stessa riga in più di un nodo di replica.  
  
-   Se si seleziona il rilevamento a livello di riga, le modifiche vengono considerate in conflitto se vengono apportate a qualsiasi colonna nella stessa riga in più di un nodo di replica (le colonne interessate nelle righe corrispondenti non devono necessariamente essere le stesse).  
  
-   Se si seleziona il rilevamento a livello di record logico, le modifiche vengono considerate in conflitto se vengono apportate a qualsiasi riga nello stesso record logico in più di un nodo di replica (le colonne interessate nelle righe corrispondenti non devono necessariamente essere le stesse).  
  
 Per altre informazioni, vedere [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
 Per specificare il livello di rilevamento e risoluzione dei conflitti di un articolo, vedere [Specify the Conflict Tracking and Resolution Level for Merge Articles](../../../relational-databases/replication/publish/specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md).  
  
## Risoluzione dei conflitti  
 Dopo il rilevamento di un conflitto, l'agente di merge avvia il sistema di risoluzione dei conflitti selezionato e lo utilizza per determinare il valore in conflitto che prevale. La riga che prevale viene applicata al server di pubblicazione e al Sottoscrittore, mentre i dati della riga non confermata vengono inseriti in una tabella dei conflitti. I conflitti vengono risolti immediatamente dopo l'esecuzione del sistema di risoluzione, a meno che non si scelga di risolvere i conflitti in modo interattivo.  
  
### Tipi di sistemi di risoluzione  
 Nella replica di tipo merge la risoluzione dei conflitti viene eseguita a livello di articolo. Per le pubblicazioni composte da numerosi articoli è possibile utilizzare diversi sistemi di risoluzione per articoli diversi oppure lo stesso sistema di risoluzione per un solo articolo, più articoli o per tutti gli articoli di una pubblicazione.  
  
 Se si desidera utilizzare il sistema di risoluzione dei conflitti predefinito basato sulle priorità, non è necessario impostare la proprietà del sistema di risoluzione di un singolo articolo. Se si desidera utilizzare un sistema di risoluzione dei conflitti di articolo anziché quello predefinito, è necessario configurare la proprietà di risoluzione per l'articolo che lo utilizzerà selezionando un sistema di risoluzione disponibile nel server di pubblicazione. Nelle proprietà delle informazioni del sistema di risoluzione è possibile specificare qualsiasi informazione specifica da trasmettere al sistema di risoluzione.  
  
 La replica di tipo merge prevede quattro tipi di sistemi di risoluzione dei conflitti:  
  
-   Il sistema di risoluzione dei conflitti predefinito basato sulla priorità  
  
     Il meccanismo di risoluzione predefinito segue una procedura diversa a seconda che la sottoscrizione sia di tipo client o server. È possibile assegnare valori di priorità ai singoli Sottoscrittori che utilizzano le sottoscrizioni server. In tal caso prevalgono le modifiche apportate al nodo con la priorità più alta. Nel caso delle sottoscrizioni client, la prima modifica scritta sul server di pubblicazione prevale nel conflitto.  
  
     Dopo la creazione di una sottoscrizione non è più possibile modificarne il tipo.  
  
-   Un gestore della logica di business  
  
     Il framework di gestione della logica di business consente di scrivere un assembly di codice gestito che viene chiamato durante il processo di sincronizzazione di tipo merge. L'assembly include la logica di business in grado di rispondere ai conflitti e altre condizioni durante la sincronizzazione. Per ulteriori informazioni, vedere [eseguire logica di Business durante la sincronizzazione di tipo Merge](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
-   Un sistema di risoluzione personalizzato basato sul modello COM  
  
     Replica di tipo merge fornisce un'API per la scrittura di sistemi di risoluzione come oggetti COM in linguaggi, ad esempio [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] o [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]. Per ulteriori informazioni, vedere [sistemi di risoluzione personalizzati basati su COM](../../../relational-databases/replication/merge/com-based-custom-resolvers.md).  
  
-   Un sistema di risoluzione basato su COM fornito da [!INCLUDE[msCoName](../../../includes/msconame-md.md)]  
  
     [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] include un numero di sistemi di risoluzione basati su COM. Per ulteriori informazioni, vedere [Microsoft sistemi di risoluzione basati su COM](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
 Per informazioni su come selezionare il tipo di sistema di risoluzione appropriato, vedere [scegliere un sistema di risoluzione](../../../relational-databases/replication/merge/choose-a-resolver.md).  
  
> [!NOTE]  
>  Alcuni sistemi di risoluzione dei conflitti di articolo sono progettati per gestire solo i conflitti di alcune operazioni. Ad esempio, un sistema di risoluzione può gestire gli aggiornamenti, ma non gli inserimenti o le eliminazioni. Il sistema di risoluzione dei conflitti predefinito basato sulla priorità gestisce qualsiasi conflitto non gestito dal sistema di risoluzione dei conflitti di articolo.  
  
 Per specificare una sottoscrizione di tipo merge e la priorità per la risoluzione dei conflitti, vedere  
  
-   [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: [Specify a Merge Subscription Type and Conflict Resolution Priority &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md)  
  
-   Replica [!INCLUDE[tsql](../../../includes/tsql-md.md)] programmazione e la programmazione di oggetti RMO (Replication Management Objects): [creare una sottoscrizione Pull](../../../relational-databases/replication/create-a-pull-subscription.md) e [creare una sottoscrizione Push](../../../relational-databases/replication/create-a-push-subscription.md)  
  
### Sistema di risoluzione interattivo  
 La replica prevede un'interfaccia utente del sistema di risoluzione interattivo che può essere utilizzata insieme al sistema di risoluzione dei conflitti predefinito basato sulla priorità o a un sistema di risoluzione dei conflitti di articolo. Quando si esegue la sincronizzazione su richiesta tramite Gestione sincronizzazione [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows, il sistema di risoluzione interattivo visualizza i dati del conflitto in fase di esecuzione e consente di selezionare il modo in cui risolvere i conflitti. Per ulteriori informazioni su come abilitare la risoluzione interattiva e avviare il sistema di risoluzione interattivo, vedere [risoluzione interattiva dei conflitti](../../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
## Visualizzazione dei conflitti  
 Il modo più diretto per visualizzare i conflitti consiste nell'utilizzare Visualizzatore conflitti di replica, disponibile in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] (anche in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sono incluse stored procedure per l'esecuzione di query nelle tabelle dei conflitti). Il Visualizzatore conflitti e il sistema di risoluzione interattivo sono strumenti simili, ma il sistema di risoluzione interattivo consente di risolvere i conflitti al momento della sincronizzazione, mentre il Visualizzatore conflitti è concepito per visualizzare i conflitti dopo la risoluzione. Se i metadati del conflitto sono ancora disponibili nelle tabelle di sistema (vengono conservati per 14 giorni per impostazione predefinita), è possibile sovrascrivere i risultati della risoluzione del conflitto nel Visualizzatore conflitti. Tuttavia, se è richiesto un intervento diretto, è consigliabile utilizzare il sistema di risoluzione interattivo.  
  
> [!NOTE]  
>  I conflitti a livello di record logici non vengono visualizzati nel Visualizzatore conflitti. Per visualizzare informazioni relative a questi conflitti, utilizzare le stored procedure di replica. Per ulteriori informazioni, vedere [visualizzare informazioni sul conflitto per le pubblicazioni di tipo Merge & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/view conflict information for merge publications.md).  
  
 Nel Visualizzatore conflitti sono visualizzate informazioni delle tre tabelle di sistema:  
  
-   La replica crea una tabella dei conflitti per ogni tabella in un articolo di merge, con un nome nel formato **msmerge_conflict _ \< PublicationName>_ \< ArticleName>**.  
  
     La struttura delle tabelle dei conflitti corrisponde a quella delle tabelle su cui sono basate. Una riga in una di queste tabelle rappresenta la versione non confermata di una riga in conflitto. La versione confermata della riga è inclusa nella tabella utente effettiva.  
  
-   Il **MSmerge_conflicts_info** tabella vengono fornite informazioni su ogni conflitto, incluso il tipo di conflitto.  
  
-   Il **sysmergearticles** tabella identifica le tabelle utente che dispone dei conflitti e fornisce informazioni sulle tabelle dei conflitti.  
  
 Per impostazione predefinita, le informazioni sui conflitti vengono archiviate:  
  
-   Nel server di pubblicazione e nel Sottoscrittore se il livello di compatibilità della pubblicazione è pari a 90RTM o superiore.  
  
-   Nel server di pubblicazione se il livello di compatibilità della pubblicazione è inferiore a 80RTM.  
  
-   Nel server di pubblicazione se i Sottoscrittori eseguono [!INCLUDE[ssEW](../../../includes/ssew-md.md)]. Impossibile archiviare dati in conflitto nel [!INCLUDE[ssEW](../../../includes/ssew-md.md)] sottoscrittori.  
  
 **Per visualizzare i conflitti**  
  
-   [! Includi [ssManStudioFull] (... / Token/ssManStudioFull_md.md)]: [View and Resolve Data Conflicts for Merge Publications &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/view and resolve data conflicts for merge publications.md)  
  
-   Replica [!INCLUDE[tsql](../../../includes/tsql-md.md)] Programming: [consente di visualizzare informazioni sui conflitti per pubblicazioni di tipo Merge & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/view conflict information for merge publications.md)  
  
## Vedere anche  
 [Sincronizzare i dati](../../../relational-databases/replication/synchronize-data.md)  
  
  