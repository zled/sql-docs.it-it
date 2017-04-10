---
title: "Creazione di script di replica | Microsoft Docs"
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
  - "script [replica di SQL Server], oggetti di replica"
  - "script di replica di tipo merge [replica di SQL Server]"
  - "replica [SQL Server], script"
  - "replica snapshot [SQL Server], creazione di script"
  - "script [replica di SQL Server]"
  - "replica transazionale, creazione di script"
ms.assetid: e50fac44-54c0-470c-a4ea-9c111fa4322b
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Creazione di script di replica
  Gli script di tutti i componenti di replica inclusi in una topologia devono essere creati come parte di un piano di ripristino di emergenza. Gli script possono inoltre essere utilizzati per automatizzare attività ripetitive. Uno script contiene le stored procedure di sistema Transact-SQL necessarie per l'implementazione dei componenti di replica, ad esempio una pubblicazione o una sottoscrizione. È possibile creare script in una procedura guidata (ad esempio la creazione guidata nuova pubblicazione) o in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dopo aver creato un componente. È possibile visualizzare, modificare ed eseguire lo script mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o **sqlcmd**. Gli script possono essere memorizzati con file di backup da utilizzare nel caso in cui sia necessario riconfigurare una topologia di replica.  
  
 È necessario creare un nuovo script per un componente se vengono apportate modifiche alle proprietà. Se si utilizzano stored procedure personalizzate con la replica transazionale, è consigliabile archiviare una copia di ogni procedura con gli script, aggiornando la copia in caso di modifica della procedura. Le procedure vengono in genere aggiornate in seguito a modifiche dello schema o a nuove esigenze applicative. Per ulteriori informazioni sulle procedure personalizzate, vedere [specificare modalità di propagazione delle modifiche per gli articoli transazionali](../../relational-databases/replication/transactional/specify-how-changes-are-propagated-for-transactional-articles.md).  
  
 Per le pubblicazioni di tipo merge che utilizzano filtri con parametri, gli script di pubblicazione contengono le chiamate alle stored procedure per la creazione di partizioni dei dati. Lo script offre un riferimento per le partizioni create e un modo per ricreare, se necessario, una o più partizioni.  
  
## Esempio di automazione di un'attività tramite script  
 Si consideri [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)], che implementa la replica di tipo merge per distribuire dati alla forza vendita remota. Una rappresentante scarica tutti i dati relativi ai clienti nella propria zona utilizzando sottoscrizioni pull. Lavorando offline, la rappresentante aggiorna i dati e immette nuovi clienti e ordini. Poiché [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] dispone di oltre cinquanta rappresentanti in zone diverse, la creazione delle diverse sottoscrizioni in ogni Sottoscrittore mediante la Creazione guidata nuova sottoscrizione richiederebbe una notevole quantità di tempo. L'amministratore della replica può invece eseguire la procedura seguente:  
  
1.  Impostare le pubblicazioni di tipo merge necessarie con partizioni basate sul rappresentante o sulla zona.  
  
2.  Creare una sottoscrizione pull per un Sottoscrittore.  
  
3.  Generare uno script basato su tale sottoscrizione pull.  
  
4.  Modificare lo script, modificando valori come il nome del Sottoscrittore.  
  
5.  Eseguire lo script in più Sottoscrittori per generare le sottoscrizioni pull necessarie.  
  
## Creazione di script per gli oggetti di replica  
 Script gli oggetti di replica da queste procedure guidate o i **replica** cartella [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Se si utilizzano le procedure guidate, è possibile scegliere di creare oggetti e includerli in script o solo di includerli in script.  
  
> [!IMPORTANT]  
>  Negli script tutte le password sono impostate come NULL. Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se si archiviano le credenziali in un file di script, è necessario proteggere il file per impedire l'accesso non autorizzato.  
  
 Per ulteriori informazioni sull'utilizzo delle procedure guidate di replica, vedere:  
  
-   [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)  
  
-   [Creazione di una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)  
  
-   [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)  
  
#### Per creare script per un oggetto da una procedura guidata di replica  
  
1.  Nel **Azioni procedura guidata** pagina di una procedura guidata, selezionare la casella di controllo appropriata per la procedura guidata:  
  
    -   **Genera un file script con i passaggi per la creazione della pubblicazione**  
  
    -   **Genera un file script con i passaggi per la creazione delle sottoscrizioni**  
  
    -   **Genera un file script con i passaggi per la configurazione della distribuzione**  
  
2.  Specificare le opzioni sulla **proprietà File di Script** pagina.  
  
3.  Completare la procedura guidata.  
  
#### Per creare script per un oggetto da Management Studio  
  
1.  Connettersi al server di distribuzione, al server di pubblicazione o al Sottoscrittore in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] e quindi espandere il nodo del server.  
  
2.  Espandere il **replica** cartella, quindi espandere il **pubblicazioni locali** cartella o il **sottoscrizioni locali** cartella.  
  
3.  Fare doppio clic su una pubblicazione o sottoscrizione e quindi fare clic su **Genera script**.  
  
4.  Specificare le opzioni nella **Genera Script SQL - \< ReplicationObject>** la finestra di dialogo.  
  
5.  Fare clic su **Genera Script nel File**.  
  
6.  Immettere un nome di file nel **percorso File Script** la finestra di dialogo e quindi fare clic su **salvare**. Viene visualizzato un messaggio di stato.  
  
7.  Fare clic su **OK**, quindi fare clic su **Chiudi**.  
  
#### Per creare script per più oggetti da Management Studio  
  
1.  Connettersi al server di distribuzione, al server di pubblicazione o al Sottoscrittore in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] e quindi espandere il nodo del server.  
  
2.  Pulsante destro del mouse il **replica** cartella e quindi fare clic su **Genera script**.  
  
3.  Specificare le opzioni nella **Genera Script SQL** la finestra di dialogo.  
  
4.  Fare clic su **Genera Script nel File**.  
  
5.  Immettere un nome di file nel **percorso File Script** la finestra di dialogo e quindi fare clic su **salvare**. Viene visualizzato un messaggio di stato.  
  
6.  Fare clic su **OK, quindi** fare clic su **Chiudi**.  
  
  