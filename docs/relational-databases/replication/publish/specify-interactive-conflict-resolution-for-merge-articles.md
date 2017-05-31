---
title: Specificare la risoluzione interattiva dei conflitti per articoli di merge | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], interactive resolvers
- interactive conflict resolution [SQL Server replication]
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: e298dea0-b5ef-4907-a745-cfad9793653f
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d488371a34cefb0ecf73824e362137243c115926
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="specify-interactive-conflict-resolution-for-merge-articles"></a>Impostazione della risoluzione interattiva dei conflitti per articoli di merge
  In questo argomento viene descritto come specificare la risoluzione interattiva dei conflitti per gli articoli di merge in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 La replica di[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] offre un sistema di risoluzione interattivo che consente di risolvere i conflitti in modo manuale durante la sincronizzazione su richiesta in Gestione sincronizzazione [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Dopo l'abilitazione della risoluzione interattiva, risolvere interattivamente i conflitti durante la sincronizzazione utilizzando il sistema di risoluzione interattivo. Il sistema di risoluzione interattivo è disponibile tramite Gestione sincronizzazione [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows. Per altre informazioni, vedere [Sincronizzare una sottoscrizione mediante Gestione sincronizzazione Microsoft Windows &#40;Gestione sincronizzazione Microsoft Windows&#41;](../../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md).  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Indicazioni](#Recommendations)  
  
-   **Per specificare la risoluzione interattiva dei conflitti per articoli di merge, utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   Se si esegue una sincronizzazione all'esterno di Gestione sincronizzazione Microsoft Windows, ad esempio una sincronizzazione pianificata o su richiesta in SQL Server Management Studio o Monitoraggio replica, i conflitti vengono risolti automaticamente senza l'intervento dell'utente, utilizzando la risoluzione dei conflitti predefinita specificata per l'articolo. Per altre informazioni, vedere [Interactive Conflict Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md).  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-enable-interactive-conflict-resolution-for-an-article"></a>Per abilitare la risoluzione interattiva dei conflitti per un articolo  
  
1.  Selezionare una tabella nella pagina **Articoli** della Creazione guidata nuova pubblicazione o nella finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per altre informazioni sull'uso della creazione guidata e l'accesso alla finestra di dialogo, vedere [Creare una pubblicazione](../../../relational-databases/replication/publish/create-a-publication.md) e [Visualizzare e modificare le proprietà della pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
2.  Fare clic su **Proprietà articolo**, quindi su **Imposta proprietà dell'articolo di tabella evidenziato** o su **Imposta proprietà di tutti gli articoli di tabelle**.  
  
3.  Nella pagina **Proprietà articolo - \<Articolo>** o **Proprietà di tutti gli articoli - \<Tipo articolo>** fare clic sulla scheda **Sistema di risoluzione**.  
  
4.  Selezionare **Consenti la risoluzione interattiva dei conflitti nel Sottoscrittore durante la sincronizzazione su richiesta**.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
6.  Se è visualizzata la finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>** fare clic su **OK** per salvare e chiudere la finestra di dialogo.  
  
#### <a name="to-specify-that-a-subscription-should-use-interactive-conflict-resolution"></a>Per specificare che in una sottoscrizione dovrà essere utilizzata la risoluzione interattiva dei conflitti  
  
1.  Nella finestra di dialogo **Proprietà sottoscrizione - \<Sottoscrittore>: \<DatabaseSottoscrizione>** specificare un valore **True** per l'opzione **Risoluzione interattiva dei conflitti**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Push Subscription Properties](../../../relational-databases/replication/view-and-modify-push-subscription-properties.md) e [View and Modify Pull Subscription Properties](../../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 È possibile impostare a livello di programmazione un Sottoscrittore in modo che utilizzi questa interfaccia grafica per risolvere conflitti relativi agli articoli quando viene creata una sottoscrizione pull di una pubblicazione di tipo merge. Nel sistema di risoluzione interattivo verranno visualizzati solo i conflitti relativi ad articoli che supportano questa opzione.  
  
#### <a name="to-create-a-merge-pull-subscription-that-uses-the-interactive-resolver"></a>Per creare una sottoscrizione pull di tipo merge che utilizza il sistema di risoluzione interattivo  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), specificando **@publication**. Notare il valore di **allow_interactive_resolver** relativo a ogni articolo nel set di risultati per il quale verrà utilizzato il sistema di risoluzione interattivo.  
  
    -   Se questo valore è **1**, il sistema di risoluzione interattivo verrà utilizzato.  
  
    -   Se questo valore è **0**, è prima necessario attivare il sistema di risoluzione interattivo per ogni articolo. A tale scopo, eseguire [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), specificando **@publication**, **@article**, il valore **allow_interactive_resolver** per **@property**e il valore **true** per **@value**.  
  
2.  Nel database di sottoscrizione del Sottoscrittore eseguire [sp_addmergepullsubscription](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md). Per altre informazioni, vedere [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
3.  Nel database di sottoscrizione del Sottoscrittore eseguire [sp_addmergepullsubscription_agent](../../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)specificando i parametri seguenti:  
  
    -   **@publisher**, **@publisher_db** (database pubblicato) e **@publication**.  
  
    -   Il valore **true** per **@enabled_for_syncmgr**.  
  
    -   Il valore **true** per **@use_interactive_resolver**.  
  
    -   Le informazioni sull'account di sicurezza richieste dall'agente di merge. Per altre informazioni, vedere [Create a Pull Subscription](../../../relational-databases/replication/create-a-pull-subscription.md).  
  
4.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addmergesubscription](../../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md).  
  
#### <a name="to-define-an-article-that-supports-the-interactive-resolver"></a>Per definire un articolo che supporta il sistema di risoluzione interattivo  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare il nome della pubblicazione cui appartiene l'articolo per **@publication**, il nome dell'articolo per **@article**, l'oggetto di database da pubblicare per **@source_object**e il valore **true** per **@allow_interactive_resolver**. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e risolvere i conflitti di dati per le pubblicazioni di tipo merge &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)   
 [Interactive Conflict Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
  
