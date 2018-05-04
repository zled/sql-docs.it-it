---
title: 'Esercitazione: Preparare SQL Server per la replica: server di pubblicazione, server di distribuzione, sottoscrittore | Microsoft Docs'
ms.custom: ''
ms.date: 04/02/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: ce30a095-2975-4387-9377-94a461ac78ee
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 1468095ba959f7baf383b68cfaab65dab2591af6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-prepare-sql-server-for-replication---publisher-distributor-subscriber"></a>Esercitazione: Preparare SQL Server per la replica: server di pubblicazione, server di distribuzione, sottoscrittore
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
È importante pianificare la sicurezza prima di configurare la topologia di replica. In questa esercitazione viene illustrato come proteggere la topologia di replica e come configurare la distribuzione, ovvero il primo passaggio nella replica dei dati. È necessario completare questa esercitazione prima delle altre esercitazioni sulla replica.  
  
> [!NOTE]  
> Per eseguire in modo protetto la replica dei dati tra server, è consigliabile seguire le indicazioni riportate in [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
Questa esercitazione illustra come preparare un server in modo che la replica possa essere eseguita in modo protetto con privilegi minimi.  

In questa esercitazione verranno illustrate le procedure per:
> [!div class="checklist"]
> * Creare account di Windows per la replica
> * Preparare la cartella per lo snapshot
> * Configurazione della distribuzione

## <a name="prerequisites"></a>Prerequisites
Questa esercitazione è destinata agli utenti che hanno familiarità con le operazioni fondamentali relative ai database ma con una conoscenza limitata delle operazioni di replica. 

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


**Tempo stimato per il completamento dell'esercitazione: 30 minuti**
  
## <a name="create-windows-accounts-for-replication"></a>Creare account di Windows per la replica
In questa sezione verranno creati account di Windows per l'esecuzione degli agenti di replica. Verrà creato un account di Windows separato nel server locale per gli agenti seguenti:  
  
|Agent|Percorso|Nome account|  
|---------|------------|----------------|  
|agente snapshot|Server di pubblicazione|<*nome_computer*>\repl_snapshot|  
|Agente di lettura log|Server di pubblicazione|<*nome_computer*>\repl_logreader|  
|Agente di distribuzione|Server di pubblicazione e Sottoscrittore|<*nome_computer*>\repl_distribution|  
|Agente di merge|Server di pubblicazione e Sottoscrittore|<*nome_computer*>\repl_merge|  
  
> [!NOTE]  
> Nelle esercitazioni sulla replica, il server di pubblicazione e il server di distribuzione condividono la stessa istanza (NODE1\SQL2016) di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mentre l'istanza del sottoscrittore (NODE2\SQL2016) è remota. Il server di pubblicazione e il Sottoscrittore possono utilizzare la stessa istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ma ciò non è un requisito. Se il server di pubblicazione e il Sottoscrittore condividono la stessa istanza, i passaggi utilizzati per creare gli account del Sottoscrittore non sono obbligatori.  

### <a name="create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>Creare account di Windows locali per gli agenti di replica nel server di pubblicazione
  
1.  Nel server di pubblicazione fare clic su **Gestione computer** in **Strumenti di amministrazione** nel Pannello di controllo.  
  
2.  In **Utilità di sistema**espandere **Utenti e gruppi locali**.  
  
3.  Fare clic con il pulsante destro del mouse su **Utenti**e quindi selezionare **Nuovo utente**.  
     
4.  Immettere **repl_snapshot** nella casella **Nome utente**, specificare la password e altre informazioni pertinenti e quindi selezionare **Crea** per creare l'account repl_snapshot: 

       ![Nuovo utente](media/tutorial-preparing-the-server-for-replication/newuser.png)
  
5.  Ripetere il passaggio precedente per creare gli account repl_logreader, repl_distribution e repl_merge:  
 
    ![Utenti di replica](media/tutorial-preparing-the-server-for-replication/replusers.png)
  
6.  Selezionare **Chiudi**.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>Per creare account di Windows locali per gli agenti di replica nel Sottoscrittore  
  
1.  Nel Sottoscrittore fare clic su **Gestione computer** in **Strumenti di amministrazione** nel Pannello di controllo.  
  
2.  In **Utilità di sistema**espandere **Utenti e gruppi locali**.  
  
3.  Fare clic con il pulsante destro del mouse su **Utenti**e quindi selezionare **Nuovo utente**.  
  
4.  Immettere **repl_distribution** nella casella **Nome utente**, specificare la password e altre informazioni pertinenti e quindi selezionare **Crea** per creare l'account repl_distribution.  
  
5.  Ripetere il passaggio precedente per creare l'account repl_merge.  
  
6.  Selezionare **Chiudi**.  

**Vedere anche**: [Panoramica degli agenti di replica](../../relational-databases/replication/agents/replication-agents-overview.md)  

## <a name="prepare-the-snapshot-folder"></a>Preparare la cartella per lo snapshot
In questa sezione si apprenderà come configurare la cartella usata per la creazione e l'archiviazione dello snapshot di pubblicazione. 

### <a name="create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>Creare una condivisione per la cartella per lo snapshot e assegnare le autorizzazioni  
  
1.  In Esplora risorse passare alla cartella di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il percorso predefinito è C:\Programmi\Microsoft SQL Server\MSSQL.X\MSSQL\Data.  
  
2.  Creare una nuova cartella denominata **repldata**.  
  
3.  Fare clic con il pulsante destro del mouse su questa cartella e selezionare **Proprietà**.  
  
    A. Nella scheda **Condivisione** della finestra di dialogo **Proprietà di repldata** selezionare **Condivisione avanzata**.  
  
    B. Nella finestra di dialogo **Condivisione avanzata** selezionare **Condividi cartella** e quindi selezionare **Autorizzazioni**:  

       ![Condivisione dei dati di replica](media/tutorial-preparing-the-server-for-replication/repldata.png)

6.  Nella finestra di dialogo **Autorizzazioni per repldata** selezionare **Aggiungi**. Nella casella di testo **Select User, Computers, Service Account, or Groups** (Seleziona utenti, computer, account del servizio o gruppi) digitare il nome dell'account dell'agente di snapshot creato in precedenza nel formato <*Nome_server_pubblicazione>***\repl_snapshot**. Selezionare **Verifica nomi** e quindi selezionare **OK**:  

    ![Aggiungere autorizzazioni di condivisione](media/tutorial-preparing-the-server-for-replication/addshareperms.png)

7. Ripetere il passaggio 6 per aggiungere gli altri due account creati in precedenza: <*Nome_server_pubblicazione>***\repl_merge** e <*Nome_server_pubblicazione>***\repl_distribution**

8. Dopo aver aggiunto queste tre account, assegnare le autorizzazioni seguenti:      
    - repl_distribution - Lettura  
    - repl_merge - Lettura  
    - repl_snapshot - Controllo completo    

  ![Autorizzazioni condivise](media/tutorial-preparing-the-server-for-replication/sharedpermissions.png)

9. Dopo aver configurato correttamente le autorizzazioni di condivisione, selezionare **OK** per chiudere la finestra di dialogo **Autorizzazioni per repldata**. Selezionare **OK** per chiudere la finestra di dialogo **Condivisione avanzata**. 

10.  In **Proprietà di repldata** selezionare la scheda **Sicurezza** e selezionare **Modifica**:  

       ![Modifica sicurezza](media/tutorial-preparing-the-server-for-replication/editsecurity.png)   

11. Nella finestra di dialogo **Autorizzazioni per repldata** selezionare **Aggiungi**. Nella casella di testo **Select User, Computers, Service Account, or Groups** (Seleziona utenti, computer, account del servizio o gruppi) digitare il nome dell'account dell'agente di snapshot creato in precedenza nel formato <*Nome_server_pubblicazione>***\repl_snapshot**. Selezionare **Verifica nomi** e quindi selezionare **OK**:  

    ![Aggiungere autorizzazioni di sicurezza](media/tutorial-preparing-the-server-for-replication/addsecuritypermissions.png)

  
12.  Ripetere il passaggio precedente per aggiungere le autorizzazioni per l'agente di distribuzione nel formato <*Nome_server_publicazione>***\repl_distribution** e per l'agente di merge nel formato <* Nome_server_pubblicazione>***\repl_merge**.  
    
  
13. Verificare che siano state concesse le autorizzazioni seguenti:  
  
    - repl_distribution - Lettura
    - repl_merge - Lettura
    - repl_snapshot - Controllo completo   
 
    ![Autorizzazioni utente sui dati della replica](media/tutorial-preparing-the-server-for-replication/replpermissions.png) 

14. Selezionare di nuovo la scheda **Condivisione** e prendere nota del **percorso di rete** per la condivisione. Questo percorso sarà necessario in seguito, al momento di configurare la **cartella per lo snapshot**:  

    ![Percorso di rete](media/tutorial-replicating-data-between-continuously-connected-servers/networkpath.png)

15. Selezionare **OK** per chiudere la finestra di dialogo **Proprietà di repldata**. 
 
**Vedere anche**:  
[Proteggere la cartella snapshot](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  

## <a name="configure-distribution"></a>Configurazione della distribuzione
In questa sezione verrà configurata la distribuzione nel server di pubblicazione e verranno impostate le autorizzazioni necessarie per i database di pubblicazione e di distribuzione. Se il server di distribuzione è già stato configurato, è necessario disabilitare la pubblicazione e la distribuzione prima di iniziare questa sezione. Non eseguire questa operazione se è necessario mantenere la topologia di replica esistente, soprattutto in un ambiente di produzione.   
  
In questa esercitazione non è prevista la configurazione del server di pubblicazione con un server di distribuzione remoto.  

### <a name="configure-distribution-at-the-publisher"></a>Configurare la distribuzione nel server di pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi espandere il nodo del server.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Replica** e selezionare **Configura distribuzione**:  

    ![Configurazione della distribuzione](media/tutorial-preparing-the-server-for-replication/configuredistribution.png)
  
    > [!NOTE]  
    > Se è stata effettuata la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando **localhost** anziché il nome effettivo del server, verrà visualizzato un avviso in cui viene indicata l'impossibilità di stabilire una connessione tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il server **'localhost'**. Selezionare **OK** nella finestra di dialogo di avviso. Nella finestra di dialogo **Connetti al server** modificare **Nome server** sostituendo **localhost** con il nome del server. Selezionare **Connetti**.  
  
    Verrà avviata la Configurazione guidata distribuzione.  
  
3.  Nella pagina **Server di distribuzione** selezionare **'NomeServer' fungerà da server di distribuzione per se stesso. Verranno creati un database di distribuzione e un log** e quindi selezionare **Avanti**:  

    ![Il server funge da server di distribuzione per se stesso](media/tutorial-preparing-the-server-for-replication/serverdistributor.png)
  
4.  Se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent non è in esecuzione, nella pagina Avvio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Agent** selezionare **Sì** e configurare l'avvio automatico del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Fare clic su **Avanti**.  

     
5.  Immettere il percorso \\\\<*Nome_server_pubblicazione>***\repldata** nella casella di testo **Cartella snapshot** e quindi selezionare **Avanti**. Questo percorso deve corrispondere a quanto visto in precedenza in **Percorso di rete** nella cartella delle proprietà di repldata dopo la configurazione delle proprietà della condivisione: 

    ![Cartella snapshot dei dati di replica](media/tutorial-preparing-the-server-for-replication/repldatasnapshot.png)
  
6.  Accettare i valori predefiniti nelle pagine rimanenti della procedura guidata:  
    
    ![Impostazioni predefinite della Distribuzione guidata](media/tutorial-preparing-the-server-for-replication/distributionwizarddefaults.png)
  
7.  Selezionare **Fine** per abilitare la distribuzione. 

    Durante la configurazione del server di distribuzione può essere visualizzato questo errore, che indica che l'account usato per avviare l'account di SQL Server Agent non è un account amministratore del sistema. È necessario avviare SQL Server Agent manualmente, concedere le autorizzazioni necessarie all'account esistente o cambiare l'account usato da SQL Server Agent: 

     ![Errore di avvio dell'agente](media/tutorial-preparing-the-server-for-replication/startingagenterror.png)

    Se SQL Server Management Studio è in esecuzione con diritti amministrativi, è possibile avviare SQL Server Agent manualmente dall'interno di SSMS:  
        ![Avviare l'agente da SSMS](media/tutorial-preparing-the-server-for-replication/ssmsstartagent.png) 

    >[!NOTE]
    > Se SQL Server Agent non sembra avviarsi, fare clic con il pulsante destro del mouse su SQL Server Agent in SSMS e quindi scegliere **Aggiorna**.  Se è ancora in stato arrestato, è necessario avviarlo manualmente da **Gestione configurazione SQL Server**.    
  
### <a name="setting-database-permissions-at-the-publisher"></a>Impostazione delle autorizzazioni per il database nel server di pubblicazione  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] espandere la cartella **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso** e quindi scegliere **Nuovo account accesso**:  

    ![Nuovo account di accesso](media/tutorial-preparing-the-server-for-replication/newlogin.png)
  
2.  Nella pagina **Generale** selezionare **Cerca**, immettere <*Nome_server_pubblicazione>***\repl_snapshot** nella casella **Immettere il nome dell'oggetto da selezionare**, selezionare **Verifica nomi** e quindi selezionare **OK**:  

    ![Aggiungere un account di accesso di replica per lo snapshot](media/tutorial-preparing-the-server-for-replication/addsnapshotlogin.png)
  
3.  Nell'elenco **Utenti con mapping all'account di accesso seguente** nella pagina **Mapping utenti** selezionare il database **e il database di** distribuzione [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
    Nell'elenco delle appartenenze a ruoli del database selezionare il ruolo **db_owner** per l'accesso a entrambi i database:  

    ![Proprietario del database dello snapshot della replica](media/tutorial-preparing-the-server-for-replication/dbowner.png)
  
4.  Selezionare **OK** per creare l'account di accesso.  
  
5.  Ripetere i passaggi 1-4 per creare un account di accesso per gli altri account locali (repl_distribution, repl_logreader e repl_merge). È necessario eseguire il mapping di questi account anche agli utenti membri del ruolo predefinito del database **db_owner** nel database di **distribuzione** e nel database **AdventureWorks**:  

    ![Utenti della replica in SSMS](media/tutorial-preparing-the-server-for-replication/usersinssms.png)
  
  
**Vedere anche**:  
[Configurare la distribuzione](../../relational-databases/replication/configure-distribution.md)  
[Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md)  

## <a name="next-steps"></a>Passaggi successivi
La preparazione del server per la replica è stata completata. Il prossimo articolo illustrerà come configurare la replica transazionale. 

Per altre informazioni, vedere l'articolo successivo
> [!div class="nextstepaction"]
> [Passaggi successivi](tutorial-replicating-data-between-continuously-connected-servers.md)

  
  
