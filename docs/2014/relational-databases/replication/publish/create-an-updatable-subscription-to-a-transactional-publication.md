---
title: Creare una sottoscrizione aggiornabile di una pubblicazione transazionale (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2014
helpviewer_keywords:
- updateable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
caps.latest.revision: 46
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1b6a3e276eb1250938e882316f84cf61f49a5b7e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290467"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-management-studio"></a>Creare una sottoscrizione aggiornabile di una pubblicazione transazionale (Management Studio)

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
Configurare le sottoscrizioni aggiornabili nella pagina **Sottoscrizioni aggiornabili** della **Creazione guidata nuova sottoscrizione**. Questa pagina è disponibile solo se è stata attivata una pubblicazione transazionale per le sottoscrizioni aggiornabili. Per altre informazioni sull'abilitazione delle sottoscrizione aggiornabili, vedere [Abilitare le sottoscrizioni aggiornabili per le pubblicazioni transazionali](enable-updating-subscriptions-for-transactional-publications.md).   
  
## <a name="to-configure-an-updatable-subscription-from-the-publisher"></a>Per configurare una sottoscrizione aggiornabile dal server di pubblicazione  

1. Connettersi al server di pubblicazione in Microsoft SQL Server Management Studio e quindi espandere il nodo del server.

2. Espandere la cartella **Replica** e quindi la cartella **Pubblicazioni locali** .

3. Fare clic col pulsante destro del mouse su una pubblicazione transazionale abilitata per l'aggiornamento di sottoscrizioni e quindi scegliere **Nuove sottoscrizioni**.

4. Seguire i passaggi della procedura guidata per specificare le opzioni della sottoscrizione, ad esempio il server nel quale deve essere eseguito l'agente di distribuzione.

5. Nella pagina **Sottoscrizioni aggiornabili** della **Creazione guidata nuova sottoscrizione** verificare che **Replica** sia selezionato.

6. Selezionare un'opzione nell'elenco a discesa **Commit nel server di pubblicazione**:

    * Per usare sottoscrizioni ad aggiornamento immediato, selezionare **Commit delle modifiche simultaneo**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento in coda (impostazione predefinita per le pubblicazioni create con la Creazione guidata nuova pubblicazione), la proprietà della sottoscrizione **update_mode** è impostata su **failover**. Questa modalità consente di passare all'aggiornamento in coda in un momento successivo se necessario.

    * Per usare sottoscrizioni ad aggiornamento in coda, selezionare **Accoda le modifiche ed esegui il commit appena possibile**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento immediato (impostazione predefinita per le pubblicazioni create con Creazione guidata nuova pubblicazione) e se il Sottoscrittore esegue SQL Server 2005 o versione successiva, la proprietà della sottoscrizione **update_mode** è impostata su queued failover. Questa modalità consente di passare all'aggiornamento immediato in un momento successivo se necessario.

    Per altre informazioni su come cambiare modalità di aggiornamento, vedere [Passare da una modalità di aggiornamento all'altra per una sottoscrizione transazionale aggiornabile](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

7. La pagina **Account di accesso per sottoscrizioni aggiornabili** viene visualizzata per le sottoscrizioni che usano l'aggiornamento immediato o la cui proprietà **update_mode** è impostata su **queued failover**. Nella pagina **Account di accesso per sottoscrizioni aggiornabili** specificare un server collegato tramite il quale vengono eseguite le connessioni al server di pubblicazione per sottoscrizioni ad aggiornamento immediato. Le connessioni vengono utilizzate dai trigger che si attivano presso il Sottoscrittore e propagano le modifiche al server di pubblicazione. Selezionare una delle opzioni seguenti:

    * **Crea un server collegato che stabilisce la connessione utilizzando l'autenticazione di SQL Server.** Selezionare questa opzione se non è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione. Durante la replica verrà creato automaticamente un server collegato. È necessario che l'account specificato esista già nel server di pubblicazione.

    * **Usa un server collegato o remoto già definito** Selezionare questa opzione se è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione tramite [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio o un altro metodo.

    Per informazioni sulle autorizzazioni necessarie per l'account di accesso al server collegato, vedere **Sottoscrizioni ad aggiornamento in coda** in [descrizione collegamento](../security/secure-the-subscriber.md).

8. Completare la procedura guidata.

## <a name="to-configure-an-updatable-subscription-from-the-subscriber"></a>Per configurare una sottoscrizione aggiornabile dal Sottoscrittore


1. Connettersi al Sottoscrittore in SQL Server Management Studio e quindi espandere il nodo del server.

2. Espandere la cartella **Replica** .

3. Fare clic col pulsante destro del mouse sulla cartella **Sottoscrizioni locali** e quindi scegliere **Nuove sottoscrizioni**.

4. Nella pagina **Pubblicazione** della **Creazione guidata nuova sottoscrizione** selezionare **Trova server di pubblicazione SQL Server** nell'elenco a discesa **Server di pubblicazione**.

5. Connettersi al server di pubblicazione nella finestra di dialogo **Connetti a server** .

6. Nella pagina **Pubblicazione** selezionare una pubblicazione transazionale abilitata per l'aggiornamento di sottoscrizioni.

7. Seguire i passaggi della procedura guidata per specificare le opzioni della sottoscrizione, ad esempio il server nel quale deve essere eseguito l'agente di distribuzione.

8. Nella pagina **Sottoscrizioni aggiornabili** della Creazione guidata nuova sottoscrizione verificare che **Replica** sia selezionato.

9. Selezionare un'opzione nell'elenco a discesa **Commit nel server di pubblicazione**:

    * Per usare sottoscrizioni ad aggiornamento immediato, selezionare **Commit delle modifiche simultaneo**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento in coda (impostazione predefinita per le pubblicazioni create con la Creazione guidata nuova pubblicazione), la proprietà della sottoscrizione **update_mode** è impostata su **failover**. Questa modalità consente di passare all'aggiornamento in coda in un momento successivo se necessario.

    * Per usare sottoscrizioni ad aggiornamento in coda, selezionare **Accoda le modifiche ed esegui il commit appena possibile**. Se si seleziona questa opzione e la pubblicazione consente sottoscrizioni ad aggiornamento immediato (impostazione predefinita per le pubblicazioni create con Creazione guidata nuova pubblicazione) e se il Sottoscrittore esegue SQL Server 2005 o versione successiva, la proprietà della sottoscrizione **update_mode** è impostata su **queued failover**. Questa modalità consente di passare all'aggiornamento immediato in un momento successivo se necessario.

    Per altre informazioni su come cambiare modalità di aggiornamento, vedere [Passare da una modalità di aggiornamento all'altra per una sottoscrizione transazionale aggiornabile](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

10. La pagina **Account di accesso per sottoscrizioni aggiornabili** viene visualizzata per le sottoscrizioni che usano l'aggiornamento immediato o la cui proprietà **update_mode** è impostata su **failover**. Nella pagina **Account di accesso per sottoscrizioni aggiornabili** specificare un server collegato tramite il quale vengono eseguite le connessioni al server di pubblicazione per sottoscrizioni ad aggiornamento immediato. Le connessioni vengono utilizzate dai trigger che si attivano presso il Sottoscrittore e propagano le modifiche al server di pubblicazione. Selezionare una delle opzioni seguenti:

    * **Crea un server collegato che stabilisce la connessione utilizzando l'autenticazione di SQL Server.** Selezionare questa opzione se non è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione. Durante la replica verrà creato automaticamente un server collegato. È necessario che l'account specificato esista già nel server di pubblicazione.

    * **Usa un server collegato o remoto già definito** Selezionare questa opzione se è stato definito un server remoto o un server collegato tra il Sottoscrittore e il server di pubblicazione tramite [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio o un altro metodo.

    Per informazioni sulle autorizzazioni necessarie per l'account di accesso al server collegato, vedere **Sottoscrizioni ad aggiornamento in coda** in [descrizione collegamento](../security/secure-the-subscriber.md).

11. Completare la procedura guidata.

## <a name="see-also"></a>Vedere anche

[Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)

[Create a Publication](create-a-publication.md)

[Creare una sottoscrizione aggiornabile di una pubblicazione transazionale con Transact-SQL](../create-updatable-subscription-transactional-publication-transact-sql.md) 
 
  
