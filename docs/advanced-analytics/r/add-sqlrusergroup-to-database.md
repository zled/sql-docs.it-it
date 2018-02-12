---
title: Aggiungere SQLRUserGroup come un utente del database | Documenti Microsoft
ms.custom: 
ms.date: 12/21/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- autenticazione implicita
- SQLRUserGroup
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Active
ms.openlocfilehash: 8e448e665044b1b8f63d30b7c99adf62419ae283
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="add-sqlrusergroup-as-a-database-user"></a>Aggiungere SQLRUserGroup come un utente del database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene illustrato come concedere al gruppo di lavoro gli account utilizzati dai servizi di machine learning in SQL Server le autorizzazioni necessarie per connettersi al database ed eseguire processi R o Python per conto dell'utente.

## <a name="what-is-sqlrusergroup"></a>Che cos'è SQLRUserGroup?

Durante l'installazione di [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] o [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)], vengono creati nuovi account utente di Windows per supportare l'esecuzione di R o Python script di attività con il token di sicurezza del [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio.

È possibile visualizzare questi account nel gruppo di utenti Windows **SQLRUserGroup**. Per impostazione predefinita, vengono creati 20 account di lavoro, che corrisponde in genere i processi più che sufficienti per l'esecuzione di apprendimento.

Quando un utente invia un machine learning script da un client esterno, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attiva un account di lavoro disponibili, ne esegue il mapping per l'identità dell'utente chiamante e viene eseguito lo script per conto dell'utente. Questo nuovo servizio del motore di database supporta l'esecuzione di script esterni, chiamato sicura *autenticazione implicita*.

Tuttavia, è necessario eseguire gli script R o Python da un client di analisi scientifica dei dati remoti, se si utilizza l'autenticazione di Windows, è necessario assegnare questi account di lavoro dell'autorizzazione per accedere al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza per conto dell'utente.

## <a name="add-sqlrusergroup-as-a-sql-server-login"></a>Aggiungere SQLRUserGroup come un account di accesso di SQL Server

1. In Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]espandere la cartella **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso**e quindi scegliere **Nuovo account di accesso**.

2. Nel **accesso - nuovo** nella finestra di dialogo **ricerca**. (Non digitare un valore nella casella ancora).
    
     ![Fare clic su Cerca per aggiungere di nuovo account di accesso per machine learning](media/implied-auth-login1.png "fare clic su Cerca per aggiungere di nuovo account di accesso per machine learning")

3. Nel **Seleziona utente o gruppo** fare clic su di **tipi di oggetto** pulsante.

     ![Ricerca di tipi di oggetto da aggiungere nuovo account di accesso per machine learning](media/implied-auth-login2.png "ricerca i tipi di oggetto da aggiungere nuovo account di accesso per machine learning")

4. Nel **tipi di oggetto** nella finestra di dialogo **gruppi**. Deselezionare tutte le altre caselle di controllo.

     ![Selezionare i gruppi nella finestra di dialogo tipi di oggetto](media/implied-auth-login3.png "selezionare gruppi nella finestra di dialogo tipi di oggetto")

4. Fare clic su **avanzate**, verificare che il percorso per la ricerca del computer corrente e quindi fare clic su **trova**.

     ![Fare clic su Trova per ottenere l'elenco di gruppi](media/implied-auth-login4.png "fare clic su Trova per ottenere l'elenco di gruppi")

5. Scorrere l'elenco di account di gruppo nel server finché non si trova un a partire da `SQLRUserGroup`.
    
    + Il nome del gruppo a cui è associato al servizio di avvio per il _istanza predefinita_ è sempre **SQLRUserGroup**, indipendentemente che sia stato installato R, Python o entrambi. Selezionare l'account per l'istanza predefinita solo.
    + Se si utilizza un _istanza denominata_, il nome dell'istanza viene aggiunto al nome del nome del gruppo di lavoro predefinito, `SQLRUserGroup`. Di conseguenza, se l'istanza è denominata "MLTEST", il nome di gruppo utente predefinito per questa istanza sarà **SQLRUserGroupMLTest**.
 
     ![Esempio di gruppi nel server](media/implied-auth-login5.png "esempio di gruppi nel server")
   
5. Fare clic su **OK** per chiudere la finestra di dialogo Ricerca avanzata.

    > [!IMPORTANT]
    > Assicurarsi che l'account corretto per l'istanza selezionata. Ogni istanza può utilizzare solo il proprio servizio di avvio e il gruppo creato per tale servizio. Le istanze non possono condividere un account di servizio o di lavoro di finestra di avvio.

6. Fare clic su **OK** per chiudere la **Seleziona utente o gruppo** la finestra di dialogo.

7. Nel **accesso - nuovo** la finestra di dialogo, fare clic su **OK**. Per impostazione predefinita, l'account di accesso viene assegnato al ruolo **public** e dispone dell'autorizzazione per connettersi al motore di database.

## <a name="change-the-number-of-worker-accounts-in-sqlrusergroup"></a>Modificare il numero di account di lavoro in SQLRUserGroup

Se si prevede un uso massiccio di machine learning, è possibile aumentare il numero di account utilizzato per eseguire gli script esterni, come descritto in questo articolo: 

+ [Modificare il pool di account utente per l'apprendimento automatico](modify-the-user-account-pool-for-sql-server-r-services.md)

Per impostazione predefinita, vengono creati 20 account, che supporta sessioni simultanee di 20. Attività parallelizzata non utilizzano gli account aggiuntivi. Ad esempio, se un utente esegue un'attività di assegnazione dei punteggi che utilizza l'elaborazione parallela, lo stesso account di lavoro vengono riutilizzate per tutti i thread.
