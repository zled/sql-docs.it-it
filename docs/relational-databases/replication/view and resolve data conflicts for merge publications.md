---
title: "Visualizzazione e risoluzione di conflitti di dati per le pubblicazioni di tipo merge (SQL Server Management Studio) | Microsoft Docs"
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
  - "risoluzione di conflitti di replica di tipo merge [replica di SQL Server], visualizzazione di conflitti"
  - "visualizzazioni di informazioni sui conflitti"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
ms.assetid: aeee9546-4480-49f9-8b1e-c71da1f056c7
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Visualizzazione e risoluzione di conflitti di dati per le pubblicazioni di tipo merge (SQL Server Management Studio)
  I conflitti nella replica di tipo merge vengono risolti in base al sistema di risoluzione specificato per ogni articolo. Per impostazione predefinita, i conflitti vengono risolti senza che sia necessario l'intervento dell'utente. È tuttavia possibile visualizzare i conflitti e modificare il risultato della risoluzione nel Visualizzatore conflitti di replica [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
 I dati dei conflitti sono disponibili nel Visualizzatore conflitti di replica per l'intervallo di tempo specificato per il periodo di memorizzazione dei conflitti, che per impostazione predefinita è di 14 giorni. Per impostare il periodo di memorizzazione dei conflitti, eseguire una delle operazioni seguenti:  
  
-   Specificare un valore di memorizzazione per il **@conflict_retention** parametro [sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md).  
  
-   Specificare un valore di **conflict_retention** per il **@property** valore parametro e un periodo di mantenimento dati per il **@value** parametro [sp_changemergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 Per impostazione predefinita, le informazioni sui conflitti vengono archiviate:  
  
-   Nel server di pubblicazione e nel Sottoscrittore se il livello di compatibilità della pubblicazione è pari a 90RTM o superiore.  
  
-   Nel server di pubblicazione se il livello di compatibilità della pubblicazione è inferiore a 80RTM.  
  
-   Nel server di pubblicazione se i Sottoscrittori eseguono [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Impossibile archiviare dati in conflitto nel [!INCLUDE[ssEW](../../includes/ssew-md.md)] sottoscrittori.  
  
 Archiviazione delle informazioni sui conflitti viene controllato per il **conflict_logging** proprietà di pubblicazione. Per ulteriori informazioni, vedere [sp_addmergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md) e [sp_changemergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md).  
  
 I conflitti possono inoltre essere risolti in modo interattivo durante la sincronizzazione tramite il sistema di risoluzione interattivo [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Il sistema di risoluzione interattivo è disponibile tramite Gestione sincronizzazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Per ulteriori informazioni, vedere [sincronizzare una sottoscrizione tramite Gestione sincronizzazione Microsoft Windows & #40; Gestione sincronizzazione Microsoft Windows & #41;](../../relational-databases/replication/synchronize a subscription using windows synchronization manager.md).  
  
### Per visualizzare e risolvere i conflitti relativi alle pubblicazioni di tipo merge  
  
1.  Connettersi al server di pubblicazione (o sottoscrittore se appropriato) in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .  
  
3.  Pulsante destro del mouse la pubblicazione per cui si desidera visualizzare i conflitti e quindi fare clic su **Visualizza conflitti**.  
  
    > [!NOTE]  
    >  Se si specifica un valore di **'subscriber'** per il **conflict_logging** proprietà, il **Visualizza conflitti** opzione di menu non è disponibile. Per visualizzare i conflitti, avviare ConflictViewer.exe dal prompt dei comandi. Per impostazione predefinita, ConflictViewer.exe si trova nella directory Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE. Per un elenco di parametri di avvio validi, eseguire ConflictViewer.exe -?.  
  
4.  Nel **Selezionare la tabella dei conflitti** la finestra di dialogo, selezionare un database di pubblicazione e di tabella per cui si desidera visualizzare i conflitti.  
  
5.  Nel Visualizzatore conflitti di replica è possibile:  
  
    -   Filtrare le righe con i pulsanti a destra della griglia superiore.  
  
    -   Selezionare una riga nella griglia superiore per visualizzare le informazioni su tale riga nella griglia inferiore.  
  
    -   Selezionare una o più righe nella griglia superiore e quindi fare clic su **rimuovere**, che equivale a scegliere il **vincitore inviare** pulsante (senza apportare modifiche ai dati).  
  
    -   Fare clic sul pulsante delle proprietà (**...**) per visualizzare ulteriori informazioni su una colonna coinvolta in un conflitto.  
  
    -   Modificare i dati di **prioritaria** o **perdente** colonna prima di inviare i dati (dati sono di sola lettura se la colonna è grigio).  
  
    -   Fare clic su **inviare vincitore** per accettare la riga designata come il vincitore del conflitto.  
  
    -   Fare clic su **inviare perdente** per eseguire l'override della risoluzione e per propagare il valore designato come ignorato del conflitto per tutti i nodi nella topologia.  
  
    -   Selezionare **registrare i dettagli del conflitto** per registrare dati in conflitto in un file. Per specificare un percorso per il file, scegliere il **visualizzazione** menu e quindi fare clic su **Opzioni**. Immettere un valore o fare clic sul pulsante Sfoglia (**...**), quindi passare al file appropriato. Fare clic su **OK** per chiudere la **Opzioni** la finestra di dialogo.  
  
6.  Chiudere il Visualizzatore conflitti di replica.  
  
## Vedere anche  
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Impostazione di un sistema di risoluzione dei conflitti dell'articolo di merge](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)  
  
  