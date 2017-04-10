---
title: "Passaggio da una modalit&#224; di aggiornamento all&#39;altra per una sottoscrizione transazionale aggiornabile | Microsoft Docs"
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
  - "replica transazionale, sottoscrizioni aggiornabili"
  - "sottoscrizioni aggiornabili, modalità di aggiornamento"
  - "sottoscrizioni [replica di SQL Server], aggiornabili"
ms.assetid: ab5ebab1-7ee4-41f4-999b-b4f0c420c921
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Passaggio da una modalit&#224; di aggiornamento all&#39;altra per una sottoscrizione transazionale aggiornabile
  In questo argomento viene descritto come passare da una modalità di aggiornamento all'altra per una sottoscrizione con transazione aggiornabile in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Per specificare la modalità per le sottoscrizioni aggiornabili, utilizzare la Creazione guidata nuova sottoscrizione. Per informazioni sull'impostazione della modalità quando si utilizza questa procedura guidata, vedere [visualizzare e modificare le proprietà di sottoscrizione Pull](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
-   **Per passare da una modalità di aggiornamento all'altra per una sottoscrizione transazionale aggiornabile, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   È possibile eseguire il failover dall'aggiornamento immediato a quello in coda in qualsiasi momento. In seguito, sarà tuttavia possibile tornare all'aggiornamento immediato solo dopo la connessione del Sottoscrittore e del server di pubblicazione e l'applicazione da parte dell'agente di lettura coda di tutti i messaggi in sospeso nella coda al server di pubblicazione.  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Se una sottoscrizione ad aggiornamento di una pubblicazione transazionale supporta il failover da una modalità di aggiornamento a un'altra, è possibile passare a livello programmatico tra le modalità di aggiornamento, al fine di gestire situazioni in cui la connettività cambia per un breve periodo di tempo. La modalità di aggiornamento può essere impostata a livello di programmazione e su richiesta utilizzando le stored procedure di replica. Per ulteriori informazioni, vedere [sottoscrizioni aggiornabili per la replica transazionale](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
> [!NOTE]  
>  Per modificare la modalità di aggiornamento dopo aver creata la sottoscrizione, il **update_mode** proprietà deve essere impostata su **failover** (che consente di passare dall'aggiornamento immediato all'aggiornamento in coda) o **in coda failover** (che consente di passare dall'aggiornamento in coda all'aggiornamento immediato) quando viene creata la sottoscrizione. Queste proprietà vengono impostate automaticamente nella Creazione guidata nuova sottoscrizione.  
  
#### Per impostare la modalità di aggiornamento per una sottoscrizione push  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]e quindi espandere il nodo del server.  
  
2.  Espandere la cartella **Replica** e quindi la cartella **Sottoscrizioni locali** .  
  
3.  Pulsante destro del mouse la sottoscrizione per il quale si desidera impostare la modalità di aggiornamento e quindi fare clic su **Imposta metodo di aggiornamento**.  
  
4.  Nel **Imposta metodo di aggiornamento - \< sottoscrittore>: \< SubscriptionDatabase>** nella finestra di dialogo **ad aggiornamento immediato** o **aggiornamento in coda**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Per impostare la modalità di aggiornamento per una sottoscrizione pull  
  
1.  Nel **Proprietà sottoscrizione - \< Publisher>: \< PublicationDatabase>** la finestra di dialogo, selezionare un valore di **immediatamente la replica delle modifiche** o **Accoda le modifiche** per il **metodo di aggiornamento del sottoscrittore** (opzione).  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 Per ulteriori informazioni sull'accesso di **Proprietà sottoscrizione - \< Publisher>: \< PublicationDatabase>** la finestra di dialogo, vedere [visualizzare e modificare le proprietà di sottoscrizione Pull](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per passare da una modalità di aggiornamento all'altra  
  
1.  Verificare che la sottoscrizione supporta il failover eseguendo [sp_helppullsubscription](../../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md) per una sottoscrizione pull o [sp_helpsubscription](../../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md) per una sottoscrizione push. Se il valore di **modalità di aggiornamento** nel set di risultati è **3** o **4**, il failover è supportato.  
  
2.  Nel database di sottoscrizione del sottoscrittore, eseguire [sp_setreplfailovermode](../../../relational-databases/system-stored-procedures/sp-setreplfailovermode-transact-sql.md). Specificare **@publisher**, **@publisher_db**, **@publication**, e uno dei seguenti valori per **@failover_mode**:  
  
    -   **in coda** -eseguire il failover all'aggiornamento in coda quando la connettività è stata temporaneamente interrotta.  
  
    -   **controllo immediato** -eseguire il failover all'aggiornamento immediato quando è stata ripristinata la connettività.  
  
## Vedere anche  
 [Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  