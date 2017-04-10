---
title: "Creare una sottoscrizione aggiornabile di una pubblicazione transazionale (Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "07/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sottoscrizioni aggiornabili transazionale"
  - "sottoscrizioni aggiornabili transazionale, SQL Server Management Studio"
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
caps.latest.revision: 51
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 51
---
# Creare una sottoscrizione aggiornabile di una pubblicazione transazionale (Management Studio)

> [!NOTE]  
>  Questa funzionalità continuerà a essere supportata nelle versioni di [!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)] dalla 2012 alla 2016.  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
Configurare le sottoscrizioni aggiornabili nel **sottoscrizioni aggiornabili** pagina di **Creazione guidata nuova sottoscrizione**. Questa pagina è disponibile solo se è stata attivata una pubblicazione transazionale per le sottoscrizioni aggiornabili. Per ulteriori informazioni sull'attivazione di sottoscrizioni aggiornabili, vedere [abilitare sottoscrizioni ad aggiornamento per le pubblicazioni transazionali](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md).   
  
## Per configurare una sottoscrizione aggiornabile dal server di pubblicazione  

1. Connettersi al server di pubblicazione in Microsoft SQL Server Management Studio e quindi espandere il nodo del server.

2. Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .

3. Fare doppio clic su una pubblicazione transazionale abilitata per sottoscrizioni aggiornabili e quindi fare clic su **nuove sottoscrizioni**.

4. Seguire i passaggi della procedura guidata per specificare le opzioni della sottoscrizione, ad esempio il server nel quale deve essere eseguito l'agente di distribuzione.

5. Nel **sottoscrizioni aggiornabili** pagina di **Creazione guidata nuova sottoscrizione**, assicurarsi **replicare** è selezionata.

6. Selezionare un'opzione di **eseguire il Commit nel server di pubblicazione** elenco a discesa:

    * Per utilizzare sottoscrizioni ad aggiornamento immediato, selezionare **commit delle modifiche simultaneo**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento in coda (il valore predefinito per le pubblicazioni create con la creazione guidata nuova pubblicazione), la proprietà della sottoscrizione **update_mode** è impostato su **failover**. Questa modalità consente di passare all'aggiornamento in coda in un momento successivo se necessario.

    * Per utilizzare le sottoscrizioni ad aggiornamento in coda, selezionare **Accoda le modifiche ed eseguire il commit quando possibile**. Se si seleziona questa opzione, la pubblicazione consente sottoscrizioni ad aggiornamento immediato (impostazione predefinita per le pubblicazioni create con la creazione guidata nuova pubblicazione) e il sottoscrittore è in esecuzione SQL Server 2005 o versioni successive, la proprietà della sottoscrizione **update_mode** è impostata su failover in coda. Questa modalità consente di passare all'aggiornamento immediato in un momento successivo se necessario.

    Per informazioni sul cambio di modalità di aggiornamento, vedere [passa tra aggiornamento modalità per una sottoscrizione transazionale aggiornabile](../../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

7. Il **account di accesso per sottoscrizioni aggiornabili** viene visualizzata la pagina per le sottoscrizioni che utilizzano l'aggiornamento immediato o con **update_mode** impostato su **in coda failover**. Nel **account di accesso per sottoscrizioni aggiornabili** pagina, specificare un server collegato in cui vengono eseguite le connessioni al server di pubblicazione per sottoscrizioni ad aggiornamento immediato. Le connessioni vengono utilizzate dai trigger che si attivano presso il Sottoscrittore e propagano le modifiche al server di pubblicazione. Selezionare una delle opzioni seguenti:

    * **Creare un server collegato che stabilisce la connessione utilizzando autenticazione di SQL Server.** Selezionare questa opzione se non è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione. Durante la replica verrà creato automaticamente un server collegato. È necessario che l'account specificato esista già nel server di pubblicazione.

    * **Usa un server collegato o remoto già definito** Selezionare questa opzione se è stato definito un server remoto o collegato tra il server di sottoscrizione e il server di pubblicazione utilizzando [sp_addserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), [sp_addlinkedserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), SQL Server Management Studio o un altro metodo.

    Per informazioni sulle autorizzazioni richieste dall'account del server collegato, vedere il **sottoscrizioni ad aggiornamento in coda** di [Immettere qui la descrizione collegamento](../../../relational-databases/replication/security/secure-the-subscriber.md).

8. Completare la procedura guidata.

## Per configurare una sottoscrizione aggiornabile dal Sottoscrittore


1. Connettersi al sottoscrittore in SQL Server Management Studio e quindi espandere il nodo del server.

2. Espandere la cartella **Replica** .

3. Pulsante destro del mouse il **sottoscrizioni locali** cartella e quindi fare clic su **nuove sottoscrizioni**.

4. Nel **pubblicazione** pagina del **Creazione guidata nuova sottoscrizione**, selezionare **trovare di pubblicazione SQL Server** dal **Publisher** elenco a discesa.

5. Connettersi al server di pubblicazione nella finestra di dialogo **Connetti a server** .

6. Selezionare una pubblicazione transazionale abilitata per sottoscrizioni ad aggiornamento nel **pubblicazione** pagina.

7. Seguire i passaggi della procedura guidata per specificare le opzioni della sottoscrizione, ad esempio il server nel quale deve essere eseguito l'agente di distribuzione.

8. Nel **sottoscrizioni aggiornabili** pagina della creazione guidata nuova sottoscrizione, verificare **replicare** è selezionata.

9. Selezionare un'opzione di **eseguire il Commit nel server di pubblicazione** elenco a discesa:

    * Per utilizzare sottoscrizioni ad aggiornamento immediato, selezionare **commit delle modifiche simultaneo**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento in coda (il valore predefinito per le pubblicazioni create con la creazione guidata nuova pubblicazione), la proprietà della sottoscrizione **update_mode** è impostato su **failover**. Questa modalità consente di passare all'aggiornamento in coda in un momento successivo se necessario.

    * Per utilizzare le sottoscrizioni ad aggiornamento in coda, selezionare **Accoda le modifiche ed eseguire il commit quando possibile**. Se si seleziona questa opzione, la pubblicazione consente sottoscrizioni ad aggiornamento immediato (impostazione predefinita per le pubblicazioni create con la creazione guidata nuova pubblicazione) e il sottoscrittore è in esecuzione SQL Server 2005 o versioni successive, la proprietà della sottoscrizione **update_mode** è impostato su in coda **failover**. Questa modalità consente di passare all'aggiornamento immediato in un momento successivo se necessario.

    Per informazioni sul cambio di modalità di aggiornamento, vedere [passa tra aggiornamento modalità per una sottoscrizione transazionale aggiornabile](../../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

10. Il **account di accesso per sottoscrizioni aggiornabili** viene visualizzata la pagina per le sottoscrizioni che utilizzano l'aggiornamento immediato o con **update_mode** messi in coda a **failover**. Nel **account di accesso per sottoscrizioni aggiornabili** pagina, specificare un server collegato in cui vengono eseguite le connessioni al server di pubblicazione per sottoscrizioni ad aggiornamento immediato. Le connessioni vengono utilizzate dai trigger che si attivano presso il Sottoscrittore e propagano le modifiche al server di pubblicazione. Selezionare una delle opzioni seguenti:

    * **Creare un server collegato che stabilisce la connessione utilizzando autenticazione di SQL Server.** Selezionare questa opzione se non è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione. Durante la replica verrà creato automaticamente un server collegato. È necessario che l'account specificato esista già nel server di pubblicazione.

    * **Usa un server collegato o remoto già definito** Selezionare questa opzione se è stato definito un server remoto o collegato tra il server di sottoscrizione e il server di pubblicazione utilizzando [sp_addserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), [sp_addlinkedserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), SQL Server Management Studio o un altro metodo.

    Per informazioni sulle autorizzazioni richieste dall'account del server collegato, vedere il **sottoscrizioni ad aggiornamento in coda** di [Immettere qui la descrizione collegamento](../../../relational-databases/replication/security/secure-the-subscriber.md).

11. Completare la procedura guidata.

## Vedere anche

[Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)

[Creazione di una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md)

[Creare una sottoscrizione aggiornabile di una pubblicazione transazionale con Transact-SQL](../../../relational-databases/replication/publish/create-updatable-subscription-to-transactional-publication.md) 
