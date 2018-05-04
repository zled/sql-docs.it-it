---
title: 'Esercitazione: Configurare la replica tra due server sempre connessi (replica transazionale) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: de374f4372f62741ff3c49a9433cf339cecf3d26
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-configure-replication-between-two-fully-connected-servers-transactional"></a>Esercitazione: Configurare la replica tra due server sempre connessi (replica transazionale)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
La replica transazionale è una buona soluzione al problema legato al trasferimento dei dati tra server con connessione continua. La procedura guidata di replica consente di eseguire in modo semplificato i passaggi necessari per configurare e amministrare una topologia di replica. Questa esercitazione illustra come configurare una topologia di replica transazionale per server con connessione continua. Per altre informazioni sul funzionamento della replica transazionale, vedere [Panoramica della replica transazionale](https://docs.microsoft.com/en-us/sql/relational-databases/replication/transactional/transactional-replication). 
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
In questa esercitazione viene descritto come pubblicare dati da un database all'altro mediante la replica transazionale. 

In questa esercitazione verranno illustrate le procedure per:
> [!div class="checklist"]
> * Creare un server di pubblicazione tramite la replica transazionale
> * Creare un sottoscrittore per il server di pubblicazione transazionale
> * Convalidare la sottoscrizione e misurare la latenza
> * Metodologia di risoluzione degli errori
  
  
## <a name="prerequisites"></a>Prerequisites  
Questa esercitazione è destinata agli utenti esperti nelle operazioni di database di base ma con una limitata conoscenza della replica. Per eseguire questa esercitazione è necessario avere completato l'esercitazione precedente [Preparazione del server per la replica](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Per consentire lo svolgimento di questa esercitazione, il sistema deve essere dotato di SQL Server Management Studio (SSMS) e di questi componenti:  
  
-   Nel server di pubblicazione (origine):  
  
    -   Una qualsiasi edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad eccezione di SQL Server Express e di SQL Compact. Questa edizioni non possono fungere da server di pubblicazione per la replica.   
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database di esempio. Per una maggiore sicurezza, i database di esempio non vengono installati per impostazione predefinita.  
  
-   Sottoscrittore (destinazione):  
  
    -   Qualsiasi edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad eccezione di [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] non può essere un Sottoscrittore nella replica transazionale.  
  
- Installare [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Installare [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Scaricare un [database campione AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Per istruzioni sul ripristino di un database in SSMS, vedere [Ripristino di un database](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 
 
>[!NOTE]
> - La replica non è supportata per server SQL Server con versioni la cui distanza sia maggiore di 2. Per altre informazioni, vedere [Supported SQL Versions in Repl Topology](https://blogs.msdn.microsoft.com/repltalk/2016/08/12/suppported-sql-server-versions-in-replication-topology/) (Versioni di SQL Server supportate nella topologia di replica).
> - In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]è necessario connettersi al server di pubblicazione e al Sottoscrittore mediante un account di accesso membro del ruolo fisso del server **sysadmin** . Per altre informazioni sul ruolo sysadmin, vedere [Ruoli a livello di server](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/server-level-roles).  
  
  
**Tempo stimato per il completamento dell'esercitazione: 60 minuti**  
  
## <a name="configure-the-publisher-for-transactional-replication"></a>Configurare il server di pubblicazione per la replica transazionale
In questa sezione verrà creata una pubblicazione transazionale con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per pubblicare un subset filtrato della tabella **Product** nel database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Verrà inoltre aggiunto l'account di accesso di SQL Server utilizzato dall'agente di distribuzione all'elenco di accesso alla pubblicazione. Per eseguire questa esercitazione è necessario avere completato l'esercitazione precedente [Preparazione del server per la replica](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).


### <a name="create-a-publication-and-define-articles"></a>Creare una pubblicazione e definire articoli
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi espandere il nodo del server.  
  
2. Fare clic con il pulsante destro del mouse su **SQL Server Agent** e selezionare **Avvia**. SQL Server Agent deve essere in esecuzione prima della creazione della pubblicazione. Se con questa operazione l'agente non si avvia, è necessario avviarlo manualmente da **Gestione configurazione SQL Server**. 
3. Espandere la cartella **Replica**, fare clic con il pulsante destro del mouse sulla cartella **Pubblicazioni locali** e selezionare **Nuova Pubblicazione**.  Verrà avviata la Creazione guidata nuova pubblicazione:  

    ![Nuova pubblicazione](media/tutorial-replicating-data-between-continuously-connected-servers/newpublication.png)
  
  
3. Nella pagina Database di pubblicazione selezionare [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] e quindi selezionare **Avanti**.  
  
4. Nella pagina Tipo di pubblicazione selezionare **Pubblicazione transazionale** e quindi selezionare **Avanti**:  

    ![Replica transazionale](media/tutorial-replicating-data-between-continuously-connected-servers/tranrepl.png)
  
5. Nella pagina Articoli espandere il nodo **Tabelle** e selezionare la casella di controllo **Product**. Espandere quindi **Product** e deselezionare le caselle di controllo accanto a **ListPrice** e a **StandardCost**. Selezionare **Avanti**:  

    ![Articoli da pubblicare](media/tutorial-replicating-data-between-continuously-connected-servers/replarticles.png)
  
6. Nella pagina Filtro righe tabella selezionare **Aggiungi**.   
  
7. Nella finestra di dialogo **Aggiungi filtro** selezionare la colonna **SafetyStockLevel**, selezionare la freccia a destra per aggiungere la colonna alla clausola WHERE in Istruzione per il filtro nella query di filtro. Digitare quindi manualmente il modificatore della clausola WHERE come segue:  
  
    ```sql  
    WHERE [SafetyStockLevel] < 500  
    ```
  
    ![Istruzione per il filtro](media/tutorial-replicating-data-between-continuously-connected-servers/filter.png)
  
8. Selezionare **OK**e quindi selezionare **Avanti**.  
  
9. Selezionare la casella di controllo **Crea uno snapshot immediatamente e mantieni lo snapshot disponibile per l'inizializzazione delle sottoscrizioni** e selezionare **Avanti**:  

    ![agente snapshot](media/tutorial-replicating-data-between-continuously-connected-servers/snapshot.png)
  
10. Nella pagina Sicurezza agente deselezionare la casella di controllo **Usa le impostazioni di sicurezza dell'agente snapshot** .   
  
    A. Selezionare **Impostazioni di sicurezza** accanto ad Agente snapshot, immettere <*Nome_server_pubblicazione>***\repl_snapshot** nella casella **Account processo**, specificare la password per l'account e quindi selezionare **OK**:  

    ![Sicurezza agente snapshot](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagentsecurity.png)
  
12. Ripetere il passaggio precedente per impostare <*Nome_server_pubblicazione*>**\repl_logreader** come account di processo per l'agente di lettura log e quindi selezionare **OK**:  

    ![Sicurezza agente di lettura log](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderagentsecurity.png)   

  
13. Nella pagina Completamento procedura guidata digitare **AdvWorksProductTrans** nella casella **Nome pubblicazione** e selezionare **Fine**:  

    ![Assegnare un nome alla pubblicazione](media/tutorial-replicating-data-between-continuously-connected-servers/advworksproducttrans.png)
  
14. Dopo la creazione della pubblicazione, selezionare **Chiudi** per completare la procedura guidata. 

    Se quando si tenta di creare la pubblicazione SQL Server Agent non è in esecuzione, può essere visualizzato l'errore riportato di seguito, che indica che la pubblicazione è stata creata ma non è stato possibile avviare l'agente di snapshot. In questo caso, è necessario avviare SQL Server Agent e quindi avviare manualmente l'agente di snapshot. Le istruzioni per eseguire questa operazione sono descritte nella sezione seguente: 

    ![Mancato avvio dell'agente di snapshot](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagenterror.png)
    
  
### <a name="to-view-the-status-of-snapshot-generation"></a>Per visualizzare lo stato della generazione dello snapshot  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e quindi la cartella **Replica** .  
  
2.  Nella cartella **Pubblicazioni locali** fare clic con il pulsante destro del mouse su **AdvWorksProductTrans** e quindi selezionare **Visualizza stato agente snapshot**:  

    ![Stato dell'agente di snapshot](media/tutorial-replicating-data-between-continuously-connected-servers/viewsnapshot.png)
  
3.  Verrà visualizzato lo stato corrente del processo dell'agente snapshot per la pubblicazione. Verificare che il processo snapshot abbia avuto esito positivo prima di passare alla sezione successiva.
          
    Se al momento della creazione della pubblicazione SQL Server Agent non era in esecuzione, l'agente di snapshot risulta 'mai eseguito' in **Visualizza stato agente snapshot** per la pubblicazione. In questo caso, selezionare **Avvia** per avviare l'agente di snapshot: 

       ![Avvia agente snapshot](media/tutorial-replicating-data-between-continuously-connected-servers/startsnapshotagent.png)
     
       Se a questo punto viene visualizzato un errore, vedere [Risolvere gli errori dell'agente di snapshot](#troubleshoot-erros-with-snapshot-agent). 

  
### <a name="to-add-the-distribution-agent-login-to-the-pal"></a>Per aggiungere l'account di accesso dell'agente di distribuzione all'elenco di accesso alla pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e quindi la cartella **Replica** .  
  
2.  Nella cartella **Pubblicazioni locali** fare clic con il pulsante destro del mouse su **AdvWorksProductTrans** e quindi selezionare **Proprietà**.  Verrà visualizzata la finestra di dialogo **Proprietà pubblicazione** .    
  
    A. Selezionare la pagina **Elenco di accesso alla pubblicazione** e selezionare **Aggiungi**.  
    B. Nella finestra di dialogo **Aggiungi accesso alla pubblicazione** selezionare <*Nome_server_pubblicazione>***\repl_distribution** e selezionare **OK**. Selezionare **OK**:

   
   ![Aggiungere un account di accesso all'elenco PAL](media/tutorial-replicating-data-between-continuously-connected-servers/tranreplproperties.png)

**Vedere anche**:  
[Concetti di base relativi alla programmazione della replica](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  

## <a name="create-a-subscription-to-the-transactional-publication"></a>Creare una sottoscrizione per la pubblicazione transazionale
In questa sezione si aggiungerà un sottoscrittore alla pubblicazione creata in precedenza. Questa esercitazione usa un sottoscrittore remoto (NODE2\SQL2016). È anche possibile, tuttavia, aggiungere localmente una sottoscrizione al server di pubblicazione. 

### <a name="to-create-the-subscription"></a>Per creare la sottoscrizione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e quindi la cartella **Replica** .  
  
2.  Nella cartella **Pubblicazioni locali** fare clic con il pulsante destro del mouse sulla pubblicazione **AdvWorksProductTrans** e quindi selezionare **Nuove sottoscrizioni**.  Verrà avviata la Creazione guidata nuova sottoscrizione: 
 
    ![Nuova sottoscrizione](media/tutorial-replicating-data-between-continuously-connected-servers/newsub.png)     
  
3.  Nella pagina Pubblicazione selezionare **AdvWorksProductTrans**e quindi Selezionare **Avanti**:  

    ![Selezionare il server di pubblicazione transazionale](media/tutorial-replicating-data-between-continuously-connected-servers/selectpub.png)
  
4.  Nella pagina Posizione in cui eseguire l'agente di distribuzione selezionare **Esegui tutti gli agenti nel database di distribuzione**e quindi selezionare **Avanti**.  Per altre informazioni sulle sottoscrizioni pull e push, vedere [Sottoscrivere le pubblicazioni](https://docs.microsoft.com/en-us/sql/relational-databases/replication/subscribe-to-publications):

    ![Esegui agenti nel database di distribuzione](media/tutorial-replicating-data-between-continuously-connected-servers/runagentsatdist.png)
  
5.  Nella pagina Sottoscrittori, se il nome dell'istanza del sottoscrittore non è visualizzato, selezionare **Aggiungi sottoscrittore** e quindi selezionare **Aggiungi Sottoscrittore SQL Server** dall'elenco a discesa. Verrà aperta la finestra di dialogo **Connetti al server**. Immettere il nome dell'istanza del sottoscrittore e quindi selezionare **Connetti**.  
    
    A. Dopo l'aggiunta del sottoscrittore, selezionare la casella accanto al nome di questo e quindi selezionare **Nuovo database** in **Database di sottoscrizione**:   

  ![Aggiungi server sottoscrittore](media/tutorial-replicating-data-between-continuously-connected-servers/addsub.png)

7. Verrà aperta la finestra di dialogo **Nuovo database**. Nella casella **Nome database** immettere **ProductReplica**, selezionare **OK** e quindi selezionare **Avanti**: 
  
    ![Database ProductReplica](media/tutorial-replicating-data-between-continuously-connected-servers/productreplica.png)
  
8.  Nella finestra di dialogo **Sicurezza agente di distribuzione** selezionare il pulsante con i tre puntini (**…**). Immettere <*Nome_server_pubblicazione>***\repl_distribution** nella casella **Account processo**, immettere la password di questo account, selezionare **OK**, e quindi selezionare **Avanti**:

    ![Aggiungi account di distribuzione](media/tutorial-replicating-data-between-continuously-connected-servers/adddistaccount.png)
  
9. Selezionare **Fine** per accettare i valori predefiniti nelle pagine rimanenti e completare la procedura guidata.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Impostazione delle autorizzazioni per il database nel Sottoscrittore  
  
1.  Connettersi al sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere la cartella **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso** e quindi selezionare **Nuovo account di accesso**.     
  
    A. Nella pagina **Generale**, in **Nome account di accesso**, selezionare **Cerca** e aggiungere l'account di accesso per <*Nome_computer_sottoscrittore>***\repl_distribution**.
    B. Nella pagina **Mapping utenti** concedere l'account di accesso **db_owner** per il database **ProductReplica**: 

    ![Accesso al sottoscrittore](media/tutorial-replicating-data-between-continuously-connected-servers/loginforsub.png)

2. Selezionare **OK** per chiudere la finestra di dialogo **Nuovo account accesso**. 

  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>Per visualizzare lo stato di sincronizzazione della sottoscrizione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e quindi la cartella **Replica** .  
  
2.  Nella cartella **Pubblicazioni locali** espandere la pubblicazione **AdvWorksProductTrans**, fare clic con il pulsante destro del mouse sulla sottoscrizione nel database **ProductReplica** e quindi selezionare **Visualizza stato sincronizzazione**. Verrà visualizzato lo stato corrente della sincronizzazione della sottoscrizione:  
    ![Visualizza stato sincronizzazione](media/tutorial-replicating-data-between-continuously-connected-servers/viewsyncstatus.png)
3.  Se la sottoscrizione non è visualizzata in **AdvWorksProductTrans**, premere F5 per aggiornare l'elenco.  
  
**Vedere anche**:  
[Inizializzare una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)  
[Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  

## <a name="measuring-replication-latency"></a>Misurazione della latenza di replica
In questa sezione si useranno token di traccia per verificare che le modifiche vengano replicate nel sottoscrittore e per determinare la latenza. La latenza è il tempo necessario perché una modifica effettuata nel server di pubblicazione sia visibile nel sottoscrittore.
  
1. Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo server, fare clic con il pulsante destro del mouse sulla cartella **Replica** e quindi selezionare **Avvia Monitoraggio replica**:

    ![Avvia Monitoraggio replica](media/tutorial-replicating-data-between-continuously-connected-servers/launchreplmonitor.png)

2. Espandere un gruppo di server di pubblicazione nel riquadro sinistro, espandere l'istanza del server di pubblicazione e quindi selezionare la pubblicazione **AdvWorksProductTrans**.  
  
    A. Selezionare la scheda **Token di traccia**.  
    B. Selezionare **Inserisci utilità di traccia**.    
    c. Visualizzare il tempo trascorso per il token di traccia nelle colonne **Dal server di pubblicazione al server di distribuzione**, **Dal server di distribuzione al Sottoscrittore**e **Latenza totale**. Il valore **In sospeso** indica che il token non ha raggiunto il punto specificato:


   ![Token di traccia](media/tutorial-replicating-data-between-continuously-connected-servers/tracertoken.png)


**Vedere anche**   
[Measure Latency and Validate Connections for Transactional Replication](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)

## <a name="error-troubleshooting-methodology"></a>Metodologia di risoluzione degli errori
Questa sezione illustra come risolvere alcuni errori di base di sincronizzazione della replica. Si tenga presente che lo scopo di questa sezione è descrivere come spostarsi tra i diversi componenti di replica con l'obiettivo di risolvere i problemi. Gli errori effettivamente visualizzati, tuttavia, possono essere diversi da quelli descritti qui e possono quindi richiedere una soluzione diversa. In questo caso, è necessaria un'ulteriore risoluzione dei problemi estranea all'ambito di questa esercitazione. 


### <a name="troubleshoot-errors-with-snapshot-agent"></a>Risolvere gli errori dell'agente di snapshot
L'**agente di snapshot** è l'agente che genera lo snapshot e lo scrive nella cartella specificata. 

1. Per visualizzare lo stato dell'agente di snapshot, espandere il nodo **Pubblicazione locale** nella replica e fare clic con il pulsante destro del mouse su **AdvWorksProductTrans** > **Visualizza stato agente snapshot** nella pubblicazione. 
2. Se in **Visualizza stato agente snapshot** viene segnalato un errore, è possibile trovare altri dettagli nella cronologia processo **Agente snapshot**. Per accedere a queste informazioni, espandere **SQL Server Agent** in **Esplora oggetti** e aprire **Monitoraggio attività processi**. 

    A. Ordinare per **Categoria** e identificare l'**agente di snapshot**  in base alla categoria 'REPL-Snapshot'. 

    B. Fare clic con il pulsante destro del mouse sull'**agente di snapshot** e selezionare **Visualizza cronologia**: 

   ![Cronologia dell'agente di snapshot](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotagenthistory.png)
    
1. Nella **cronologia dell'agente di snapshot** selezionare la voce di log pertinente, in genere una linea o due *prima* della voce con la segnalazione dell'errore (gli errori sono indicati da una X rossa).  Esaminare il testo del messaggio nella casella di testo sotto i log: 

    ![Accesso negato all'agente di snapshot](media/tutorial-replicating-data-between-continuously-connected-servers/snapshotaccessdenied.png)

        The replication agent had encountered an exception.
        Exception Message: Access to path '\\node1\repldata.....' is denied.


  Se le autorizzazioni di Windows dell'utente per la cartella dello snapshot non sono configurate correttamente, viene visualizzato l'errore 'accesso negato' per l'**agente di snapshot**. È necessario verificare le autorizzazioni dell'account <*Nome_server_pubblicazione>***\repl_snapshot** per la cartella repldata. Per altre informazioni, vedere [Creare una condivisione per la cartella per lo snapshot e assegnare le autorizzazioni](tutorial-preparing-the-server-for-replication.md#create-a-share-for-the-snapshot-folder-and-assign-permissions).

### <a name="troubleshoot-errors-with-log-reader-agent"></a>Risolvere gli errori dell'agente di lettura log
L'**agente di lettura log** si connette al database del server di pubblicazione e analizza il log delle transazioni per tutte le transazioni contrassegnate 'per la replica'. Aggiunge quindi queste transazioni al database di **distribuzione**. 

1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo server, fare clic con il pulsante destro del mouse sulla cartella **Replica** e quindi selezionare **Avvia Monitoraggio replica**:  

    ![Avviare Monitoraggio replica](media/tutorial-replicating-data-between-continuously-connected-servers/launchreplmonitor.png)
  
    Verrà avviato Monitoraggio replica: ![Monitoraggio replica](media/tutorial-replicating-data-between-continuously-connected-servers/replmonitor.png) 
   
2. La X rossa indica che la pubblicazione non viene sincronizzata. Espandere **Server di pubblicazione personali** sul lato sinistro e quindi espandere il server di pubblicazione pertinente.  
  
3.  Selezionare la pubblicazione **AdvWorksProductTrans** a sinistra e quindi cercare la X rossa in una delle schede per identificare dove risiede il problema. In questo caso, la X rossa è sulla **scheda Agenti** e indica che per uno degli agenti si è verificato un errore: 

    ![Errore dell'agente](media/tutorial-replicating-data-between-continuously-connected-servers/agenterror.png)

4. Selezionare la **scheda Agenti** per identificare l'agente per il quale è stato rilevato l'errore: 

    ![Errore di lettura log](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderagentfailure.png)


5. Questa visualizzazione include due agenti, l'**agente di snapshot** e l'**agente di lettura log**. Quello per il quale si è verificato un errore avrà la X rossa. In questo caso, l'**agente di lettura log** ha la X rossa, che indica la presenza di un problema. Fare doppio clic sulla riga con la segnalazione dell'errore, in questo caso l'**agente di lettura log**. Verrà avviata la **Cronologia agente** per l'agente selezionato, in questo caso l'**agente di lettura log**, con altre informazioni sull'errore: 
    
    ![Errore di lettura log](media/tutorial-replicating-data-between-continuously-connected-servers/logreadererror.png)

       Status: 0, code: 20011, text: 'The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.'.
       The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.
       Status: 0, code: 15517, text: 'Cannot execute as the database principal because the principal "dbo" does not exist, this type of principal cannot be impersonated, or you do not have permission.'.
       Status: 0, code: 22037, text: 'The process could not execute 'sp_replcmds' on 'NODE1\SQL2016'.'.        

6. L'errore riportato sopra viene in genere visualizzato perché il proprietario del database di pubblicazione non è impostato correttamente. Ciò accade solitamente quando il database è stato ripristinato. Per verificarlo, espandere **Database** in **Esplora oggetti** > fare clic con il pulsante destro del mouse su **AdventureWorks2012** > **Proprietà**. Verificare l'esistenza di un proprietario nella pagina **File**. Se questo campo è vuoto, questa è la causa probabile del problema: 

    ![Proprietà del database](media/tutorial-replicating-data-between-continuously-connected-servers/dbproperties.png)

7. Se il proprietario è vuoto nella pagina **File**, aprire una **Nuova finestra di query** all'interno del contesto del database **AdventureWorks2012**. Eseguire il frammento di codice T-SQL seguente:

    ```sql
    -- set the owner of the database to 'sa' or a specific user account, without the brackets. 
    EXEC sp_changedbowner '<useraccount>'
    -- example for sa: exec sp_changedbowner 'sa'
    -- example for user account: exec sp_changedbowner 'sqlrepro\administrator' 
    ```

8. Sarà necessario riavviare l'**agente di lettura log**. A tale scopo, espandere il nodo **SQL Server Agent** in **Esplora oggetti** e aprire **Monitoraggio attività processi**. Ordinare per **Categoria** e identificare l'**agente di lettura Log** in base alla categoria **'REPL-LogReader'**. Fare clic con il pulsante destro del mouse sul processo dell'**agente di lettura log** e selezionare **Inizia processo al passaggio**: 

    ![Riavviare l'agente di lettura log](media/tutorial-replicating-data-between-continuously-connected-servers/startjobatstep.png)

9. Verificare che la pubblicazione venga sincronizzata aprendo di nuovo **Monitoraggio replica**. Se non è già aperto, è possibile trovarlo facendo clic con il pulsante destro del mouse su **Replica** in **Esplora oggetti**. 
10. Selezionare la pubblicazione **AdvWorksProductTrans**, selezionare la scheda **Agenti** e fare doppio clic sull'**agente di lettura log** per aprire la cronologia dell'agente. È ora possibile vedere l'**agente di lettura log** in esecuzione, nonché i comandi di replica oppure il messaggio "Nessuna transazione replicata disponibile":

    ![Lettura log in esecuzione](media/tutorial-replicating-data-between-continuously-connected-servers/logreaderrunning.png)

### <a name="troubleshoot-errors-with-distribution-agent"></a>Risolvere gli errori dell'agente di distribuzione
L'**agente di distribuzione** prende i dati che trova nel database di **distribuzione** e quindi li applica al sottoscrittore. 

1. Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo server, fare clic con il pulsante destro del mouse sulla cartella **Replica** e quindi selezionare **Avvia Monitoraggio replica**.  
2. In **Monitoraggio replica** selezionare la pubblicazione **AdvWorksProductTrans** e selezionare la scheda **Tutte le sottoscrizioni**. Fare clic con il pulsante destro del mouse sulla sottoscrizione e scegliere **Visualizza dettagli**:

    ![Visualizza i dettagli della distribuzione](media/tutorial-replicating-data-between-continuously-connected-servers/viewdetails.png)

2. Verrà visualizzata la finestra di dialogo **Cronologia database di distribuzione - Sottoscrittore** con l'indicazione chiara dell'errore riscontrato per l'agente: 

     ![Errore nella cronologia dell'agente di distribuzione](media/tutorial-replicating-data-between-continuously-connected-servers/disthistoryerror.png)
    
        Error messages:
        Agent 'NODE1\SQL2016-AdventureWorks2012-AdvWorksProductTrans-NODE2\SQL2016-7' is retrying after an error. 89 retries attempted. See agent job history in the Jobs folder for more details.

3. L'errore indica che l'**agente di distribuzione** esegue nuovi tentativi. Per scoprire altre informazioni, espandere **SQL Server Agent** in **Esplora oggetti** > **Monitoraggio attività processi**. Ordinare i processi per **Categoria**. 

    A. Identificare l'**agente di distribuzione** in base alla categoria **'REPL-Distribution'**. Fare clic con il pulsante destro del mouse sull'agente e scegliere **Visualizza cronologia**:

    ![Visualizza la cronologia dell'agente di distribuzione](media/tutorial-replicating-data-between-continuously-connected-servers/viewdistagenthistory.png)

5. Selezionare una delle voci dell'errore e visualizzare il testo corrispondente nella parte inferiore della finestra:  

    ![Password errata per l'agente di distribuzione](media/tutorial-replicating-data-between-continuously-connected-servers/distpwwrong.png)
    
        Message:
        Unable to start execution of step 2 (reason: Error authenticating proxy NODE1\repl_distribution, system error: The user name or password is incorrect.)

6. L'errore indica che la password usata dall'**agente di distribuzione** non è corretta. Per risolvere questo problema, espandere il nodo **Replica** in **Esplora oggetti**, fare clic con il pulsante destro del mouse sulla sottoscrizione > **Proprietà**. Selezionare i puntini di sospensione (...) accanto a **Account processo agente** e modificare la password:

    ![Modificare la password per l'agente di distribuzione](media/tutorial-replicating-data-between-continuously-connected-servers/distagentpwchange.png)

7. Controllare di nuovo **Monitoraggio replica**, che è possibile trovare facendo clic con il pulsante destro del mouse su **Replica** in **Esplora oggetti**. Una X rossa in **Tutte le sottoscrizioni** indica che per l'**agente di distribuzione** si verifica ancora un errore. Aprire **Cronologia database di distribuzione - Sottoscrittore** facendo clic con il pulsante destro del mouse sulla sottoscrizione in **Monitoraggio replica** > **Visualizza dettagli**. In questo caso, l'errore è diverso: 

    ![L'agente di distribuzione non riesce a connettersi](media/tutorial-replicating-data-between-continuously-connected-servers/distagentcantconnect.png)
           
        Connecting to Subscriber 'NODE2\SQL2016'        
        Agent message code 20084. The process could not connect to Subscriber 'NODE2\SQL2016'.
        Number:  18456
        Message: Login failed for user 'NODE2\repl_distribution'.

8. Questo errore indica che l'**agente di distribuzione** non è in grado di connettersi al sottoscrittore, perché l'accesso non riesce per l'utente **NODE2\repl_distribution**. Per analizzare ulteriormente il problema, connettersi al sottoscrittore e aprire il *log degli errori di SQL Server* **corrente** nel nodo **Gestione** in **Esplora oggetti**: 

    ![Accesso non riuscito per il sottoscrittore](media/tutorial-replicating-data-between-continuously-connected-servers/loginfailed.png) Se viene visualizzato questo errore, nel sottoscrittore manca l'account di accesso. Per risolvere questo problema, vedere [Impostazione delle autorizzazioni per il database nel sottoscrittore](#setting-database-permissions-at-the-subscriber).

9. Dopo aver risolto l'errore di accesso, controllare di nuovo **Monitoraggio replica**. Se tutti i problemi sono stati risolti, si noterà una freccia verde accanto al **nome della pubblicazione** e lo stato **In esecuzione** in **Tutte le sottoscrizioni**. Fare clic con il pulsante destro del mouse sulla **sottoscrizione** per avviare di nuovo **Cronologia database di distribuzione - Sottoscrittore** e verificare l'esito positivo. Se si tratta della prima esecuzione dell'agente di distribuzione, si noterà che è stata eseguita la copia bulk dello snapshot nel sottoscrittore, come illustrato nella figura seguente: 

     ![Operazione dell'agente di distribuzione riuscita](media/tutorial-replicating-data-between-continuously-connected-servers/distagentsuccess.png)   

  ## <a name="next-steps"></a>Passaggi successivi
È stata eseguita la configurazione sia del server di pubblicazione che del sottoscrittore per la replica transazionale.  È ora possibile inserire, aggiornare o eliminare dati nella tabella **Product** nel server di pubblicazione. È anche possibile eseguire una query nella tabella **Product** dal sottoscrittore per visualizzare le modifiche replicate. Il prossimo articolo descrive come configurare la replica di tipo merge.  

Per altre informazioni, vedere l'articolo successivo
> [!div class="nextstepaction"]
> [Passaggi successivi](tutorial-replicating-data-with-mobile-clients.md)

  
