---
title: "Sottoscrittori | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.subscribers.f1"
helpviewer_keywords: 
  - "Sottoscrittori [Replica di SQL Server]"
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Sottoscrittori
  Specificare il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sottoscrittori che riceveranno una sottoscrizione della pubblicazione selezionata.  
  
## Opzioni  
 **Sottoscrittori**  
 Selezionare la casella di controllo nella griglia per abilitare il corrispondente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] origine dati come sottoscrittore della pubblicazione scelta nella **pubblicazione** pagina. Se il Sottoscrittore non è incluso nell'elenco, fare clic su **Aggiungi Sottoscrittore** o su **Aggiungi Sottoscrittore SQL Server**.  
  
 **Database di sottoscrizione**  
 Le informazioni visualizzate in e le azioni disponibili in questa colonna dipendono dal tipo di sottoscrittore visualizzato nella **sottoscrittori** colonna:  
  
-   Per i Sottoscrittori [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selezionare un database di sottoscrizione nell'elenco **Database di sottoscrizione** oppure creare un nuovo database selezionando il comando **Nuovo database** nello stesso elenco.  
  
    > [!NOTE]  
    >  Se si sta abilitando il server di pubblicazione come Sottoscrittore, il database di sottoscrizione deve essere diverso dal database di pubblicazione.  
  
-   Il database di sottoscrizione non viene visualizzato per i Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Specificare il database, insieme ad altre informazioni di connessione, nel **nome dell'origine dati** campo di **aggiungere Non SQL Server** la finestra di dialogo. Questa finestra di dialogo è disponibile facendo **Aggiungi Sottoscrittore** e quindi fare clic su **Aggiungi Sottoscrittore Non SQL Server**.  
  
 **Aggiungi Sottoscrittore**  
 Consente di aggiungere un server all'elenco dei server attivabili come Sottoscrittori. Questo pulsante viene visualizzato se vengono soddisfatte tutte le condizioni seguenti:  
  
-   La pubblicazione selezionata è una pubblicazione snapshot o transazionale che non supporta le sottoscrizioni aggiornabili.  
  
    > [!NOTE]  
    >  Se la pubblicazione che si sta sottoscrivendo dispone di sottoscrizioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e non è ancora abilitata per i Sottoscrittori non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], non è possibile aggiungere una sottoscrizione non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   La sottoscrizione è una sottoscrizione push.  
  
-   Nel server di pubblicazione della pubblicazione selezionata è in esecuzione [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] o versione successiva.  
  
 Fare clic su **Aggiungi Sottoscrittore** viene visualizzato un menu con due opzioni: **Aggiungi Sottoscrittore SQL Server** e **Aggiungi Sottoscrittore Non SQL Server**. Fare clic su **Aggiungi Sottoscrittore Non SQL Server** per aggiungere un Oracle o un sottoscrittore IBM DB2.  
  
 **Aggiungi Sottoscrittore SQL Server**  
 Consente di aggiungere un server all'elenco dei server attivabili come Sottoscrittori. Questo pulsante viene visualizzato se viene soddisfatta una o più delle condizioni seguenti:  
  
-   La pubblicazione selezionata è una pubblicazione di tipo merge, snapshot o transazionale che supporta le sottoscrizioni aggiornabili.  
  
-   La sottoscrizione è una sottoscrizione pull.  
  
-   Nel server di pubblicazione della pubblicazione selezionata è in esecuzione una versione di SQL Server precedente a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Per le versioni precedenti il pulsante viene visualizzato solo se viene soddisfatta una o più delle condizioni seguenti:  
  
    -   L'utente è membro del ruolo predefinito del server **sysadmin** nel server di pubblicazione.  
  
    -   Il Sottoscrittore è stato aggiunto nella pagina **Sottoscrittori** della finestra di dialogo **Proprietà server di pubblicazione** .  
  
    -   La pubblicazione consente le sottoscrizioni anonime.  
  
## Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Sottoscrittori non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  