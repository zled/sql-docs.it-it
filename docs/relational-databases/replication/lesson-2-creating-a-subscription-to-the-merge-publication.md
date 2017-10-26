---
title: 'Lezione 2: Creazione di una sottoscrizione per una pubblicazione di tipo merge | Microsoft Docs'
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 06722baa-9065-443e-b1d5-99036cf89074
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 423ad3b42e75c70e6826e04a298c5eac4e590291
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-2-creating-a-subscription-to-the-merge-publication"></a>Lezione 2: Creazione di una sottoscrizione per una pubblicazione di tipo merge
In questa lezione verranno descritte le procedure per creare una sottoscrizione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Verranno quindi impostate le autorizzazioni per il database di sottoscrizione e verrà generato manualmente lo snapshot dei dati filtrati per la nuova sottoscrizione. Per eseguire questa lezione è necessario aver completato la lezione precedente [Lezione 1: Pubblicazione dei dati tramite la replica di tipo merge](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md).  
  
### <a name="to-create-the-subscription"></a>Per creare la sottoscrizione  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server, espandere la cartella **Replica** , fare clic con il pulsante destro del mouse sulla cartella **Sottoscrizioni locali** e scegliere **Nuova sottoscrizione**.  
  
    Verrà avviata la Creazione guidata nuova sottoscrizione.  
  
2.  Nella pagina **Pubblicazione** selezionare **Trova server di pubblicazione SQL Server** nell'elenco **Server di pubblicazione** .  
  
3.  Nella finestra di dialogo **Connetti al server** immettere il nome dell'istanza del server di pubblicazione nella casella **Nome server** e fare clic su **Connetti**.  
  
4.  Fare clic su **AdvWorksSalesOrdersMerge**e su **Avanti**.  
  
5.  Nella pagina Posizione in cui eseguire l'agente di merge fare clic su **Esegui ogni agente nel relativo Sottoscrittore**e su **Avanti**.  
  
6.  Nella pagina Sottoscrittori selezionare il nome dell'istanza del server del sottoscrittore e selezionare **dall'elenco in**Database di sottoscrizione **<New Database>** .  
  
7.  Nella finestra di dialogo **Nuovo database** immettere **SalesOrdersReplica** nella casella **Nome database** , selezionare **OK**e fare clic su **Avanti**.  
  
8.  Nella pagina Sicurezza agente di merge fare clic sul pulsante con i puntini di sospensione (**…**), immettere \<*Nome_computer>***\repl_merge** nella casella **Account processo**, specificare la password per l'account, fare clic su **OK**, su **Avanti** e di nuovo su **Avanti**.  
  
9. Nella pagina Inizializzazione sottoscrizioni selezionare **Alla prima sincronizzazione** dall'elenco **Quando** , fare clic su **Avanti**e di nuovo su **Avanti** .  
  
10. Nella pagina Valori HOST_NAME immettere un valore pari a **adventure-works\pamela0** nella casella **Valore HOST_NAME** e fare clic su **Fine**.  
  
11. Fare di nuovo clic su **Fine** e dopo aver creato la sottoscrizione fare clic su **Chiudi**.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Impostazione delle autorizzazioni per il database nel Sottoscrittore  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere **Database**, **SalesOrdersReplica**e **Sicurezza**, fare clic con il pulsante destro del mouse su **Utenti**e scegliere **Nuovo utente**.  
  
2.  Nella pagina **Generale** immettere \<*Nome_computer>***\repl_merge** nella casella **Nome utente**, fare clic sul pulsante con i puntini di sospensione (**…**), fare clic su **Sfoglia**, selezionare \<*Nome_computer>***\repl_merge**, fare clic su **OK**, su **Controlla nomi** e su **OK**.  
  
3.  In **Appartenenza a ruoli del database**selezionare **db_owner**e fare clic su **OK** per creare l'utente.  
  
### <a name="to-create-the-filtered-data-snapshot-for-the-subscription"></a>Per creare lo snapshot dei dati filtrati per la sottoscrizione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e la cartella **Replica** .  
  
2.  Nella cartella **Pubblicazioni locali** fare clic con il pulsante destro del mouse sulla pubblicazione **AdvWorksSalesOrdersMerge** e scegliere **Proprietà**.  
  
    Verrà visualizzata la finestra di dialogo **Proprietà pubblicazione** .  
  
3.  Selezionare la pagina **Partizioni dati** e fare clic su **Aggiungi**.  
  
4.  Nella finestra di dialogo **Aggiungi partizione dati** digitare **adventure-works\pamela0** nella casella **Valore HOST_NAME** e fare clic su **OK**.  
  
5.  Selezionare la partizione appena aggiunta, selezionare **Genera gli snapshot selezionati adesso**e fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
In questo modo è stata creata una sottoscrizione per la pubblicazione di tipo merge ed è stato generato lo snapshot dei dati filtrati per la nuova partizione dati della sottoscrizione in modo che sia disponibile all'inizializzazione della sottoscrizione. Il passaggio successivo consiste nella concessione dei diritti all'agente di merge nel database di sottoscrizione e nell'esecuzione dell'agente di merge per l'avvio della sincronizzazione e l'inizializzazione della sottoscrizione. Vedere [Lezione 3: Sincronizzazione della sottoscrizione con la pubblicazione di tipo merge](../../relational-databases/replication/lesson-3-synchronizing-the-subscription-to-the-merge-publication.md).  
  
## <a name="see-also"></a>Vedere anche  
[Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
[Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)  
[Snapshot per pubblicazioni di tipo merge con filtri con parametri](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  

