---
title: "Visualizzazione di conflitti di dati per le pubblicazioni transazionali (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "risoluzione del conflitto [replica di SQL Server], aggiornamento sottoscrizioni in coda"
  - "sottoscrizioni ad aggiornamento in coda [replica di SQL Server]"
  - "visualizzazioni di informazioni sui conflitti"
ms.assetid: 9977dd75-b0de-4376-9c13-86d80567d8aa
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Visualizzazione di conflitti di dati per le pubblicazioni transazionali (SQL Server Management Studio)
  Il Visualizzatore conflitti di replica [!INCLUDE[msCoName](../../includes/msconame-md.md)] consente di visualizzare i conflitti per la replica transazionale peer-to-peer e per la replica transazionale con sottoscrizioni ad aggiornamento in coda. Per informazioni su come rilevare e risolvere i conflitti, vedere [il rilevamento dei conflitti nella replica Peer-to-Peer](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md) e [impostare in coda l'aggiornamento di conflitto di opzioni di risoluzione & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/publish/set-queued-updating-conflict-resolution-options-sql-server-management-studio.md).  
  
 La disponibilità di dati dei conflitti dipende dal tipo di replica e dal periodo di memorizzazione dei conflitti:  
  
-   Per la replica peer-to-peer, per impostazione predefinita quando viene rilevato un conflitto si verifica un errore dell'agente di distribuzione. Nel log degli errori viene registrato un errore di conflitto, ma nella tabella dei conflitti non vengono registrati dati, che non sono quindi disponibili per la visualizzazione. Se l'esecuzione dell'agente di distribuzione può continuare, viene registrato localmente un conflitto in ogni nodo in cui è stato rilevato. Per ulteriori informazioni, vedere "Gestione dei conflitti" in [il rilevamento dei conflitti nella replica Peer-to-Peer](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md).  
  
-   Per le sottoscrizioni ad aggiornamento in coda, sono disponibili dati per ogni conflitto. I dati dei conflitti sono disponibili nel Visualizzatore conflitti di replica per l'intervallo di tempo specificato per il periodo di memorizzazione dei conflitti, che per impostazione predefinita è di 14 giorni. Per impostare il periodo di memorizzazione dei conflitti, eseguire una delle operazioni seguenti:  
  
    -   Specificare un valore di conservazione per il parametro @conflict_retention di [sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md).  
  
    -   Specificare un valore di **'conflict_retention'** per il parametro @property e un valore di conservazione per il parametro @value di [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md).  
  
### Per visualizzare i conflitti  
  
1.  Connettersi al server appropriato in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi espandere il nodo del server:  
  
    -   Per la replica peer-to-peer, si tratta del nodo in cui si è verificato il conflitto.  
  
    -   Per le sottoscrizioni ad aggiornamento in coda, si tratta di server di pubblicazione.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Pulsante destro del mouse la pubblicazione per cui si desidera visualizzare i conflitti e quindi fare clic su **Visualizza conflitti**.  
  
4.  Nel **Selezionare la tabella dei conflitti** la finestra di dialogo, selezionare un database di pubblicazione e di tabella per cui si desidera visualizzare i conflitti.  
  
5.  Nel Visualizzatore conflitti di replica è possibile:  
  
    -   Filtrare le righe con i pulsanti a destra della griglia superiore.  
  
    -   Selezionare una riga nella griglia superiore per visualizzare le informazioni su tale riga nella griglia inferiore.  
  
    -   Selezionare una o più righe nella griglia superiore e quindi fare clic su **rimuovere**, che rimuove la riga dalla tabella dei metadati dei conflitti.  
  
    -   Fare clic sul pulsante delle proprietà (**...**) per visualizzare ulteriori informazioni su una colonna coinvolta in un conflitto.  
  
    -   Selezionare **registrare i dettagli del conflitto** per registrare dati in conflitto in un file. Per specificare un percorso per il file, scegliere il **visualizzazione** menu e quindi fare clic su **Opzioni**. Immettere un valore o fare clic sul pulsante Sfoglia (**...**), quindi passare al file appropriato. Fare clic su **OK** per chiudere la **Opzioni** la finestra di dialogo.  
  
6.  Chiudere il Visualizzatore conflitti di replica.  
  
## Vedere anche  
 [Replica transazionale peer-to-peer](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Rilevamento e risoluzione dei conflitti nell'aggiornamento in coda](../../relational-databases/replication/transactional/queued-updating-conflict-detection-and-resolution.md)  
  
  