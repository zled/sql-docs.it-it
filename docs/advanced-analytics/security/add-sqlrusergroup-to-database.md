---
title: Aggiungere SQLRUserGroup come utente del database (SQL Server Machine Learning Services) | Microsoft Docs
description: Come aggiungere SQLRUserGroup come utente del database per SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: fc5294453def64d13cc43a74a8a5fb299c3e23e3
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100322"
---
# <a name="add-sqlrusergroup-as-a-database-user"></a>Aggiungere SQLRUserGroup come utente del database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Creare un account di accesso di database per il [SQLRUserGroup](../concepts/security.md#sqlrusergroup) per consentire le connessioni attendibili provenienti da script R e Python, se la destinazione sono dati o le operazioni nell'istanza di SQL Server. 

Per gli script che contiene le stringhe di connessione con gli account di accesso di SQL Server o un nome utente completo e una password, la creazione di un account di accesso non è obbligatoria.

## <a name="when-a-login-is-required"></a>Quando è necessario un account di accesso

Se lo script R o Python include una stringa di connessione che specifica una connessione trusted (ad esempio, "Trusted_Connection = True"), è una configurazione aggiuntiva necessaria per la presentazione corretta dell'identità dell'utente per SQL Server. Per i processi esterni in esecuzione con un **SQLRUserGroup** account di lavoro, ad esempio MSSQLSERVER01, l'utente attendibile viene presentato come l'identità di lavoro. Poiché questa identità non dispone di alcun diritto di accesso di SQL Server, attendibili le connessioni non riusciranno a meno che non si aggiungono **SQLRUserGroup** come utente del database. Per altre informazioni, vedere [ *l'autenticazione implicita*](../../advanced-analytics/concepts/security.md#implied-authentication).

È importante ricordare che Launchpad conserva un mapping dell'utente originale che ha richiamato lo script e l'account di lavoro che esegue il processo. Dopo aver stabilito la connessione trusted per l'account di lavoro, l'identità dell'utente chiamante originale subentra e viene usato per recuperare i dati. Non è necessario concedere le autorizzazioni db_datareader per **SQLRUserGroup**.

> [!Note]
>  Verificare che l'opzione **SQLRUserGroup** disponga delle autorizzazioni "Consenti accesso locale". Per impostazione predefinita, questo diritto viene assegnato a tutti i nuovi utenti locali, ma in alcune organizzazioni potrebbero essere applicati criteri di gruppo più rigorosi.

## <a name="create-a-login"></a>Crea un accesso

1. In Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]espandere la cartella **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso**e quindi scegliere **Nuovo account di accesso**.

2. Nel **account di accesso - nuovo** finestra di dialogo **ricerca**. (Non digitare qualsiasi elemento nella finestra di ancora).
    
     ![Fare clic su Cerca per aggiungere nuovi account di accesso per machine learning](media/implied-auth-login1.png "fare clic su Cerca per aggiungere nuovi account di accesso per machine learning")

3. Nel **Seleziona utente o gruppo** fare clic sui **tipi di oggetto** pulsante.

     ![Cerca tipi di oggetto per aggiungere nuovi account di accesso per machine learning](media/implied-auth-login2.png "Cerca tipi di oggetto per aggiungere nuovi account di accesso per machine learning")

4. Nel **tipi di oggetti** finestra di dialogo **gruppi**. Deselezionare tutte le altre caselle di controllo.

     ![Selezionare i gruppi nella finestra di dialogo tipi di oggetti](media/implied-auth-login3.png "Seleziona gruppi nella finestra di dialogo tipi di oggetto")

4. Fare clic su **avanzate**, verificare che la posizione in cui cercare il computer corrente e quindi fare clic su **trova ora**.

     ![Fare clic su Trova per ottenere l'elenco dei gruppi](media/implied-auth-login4.png "fare clic su Trova per ottenere l'elenco dei gruppi")

5. Scorrere l'elenco degli account di gruppo nel server fino a individuare che inizia con `SQLRUserGroup`.
    
    + Il nome del gruppo di cui è associato il servizio Launchpad per il _istanza predefinita_ è sempre **SQLRUserGroup**, indipendentemente dal fatto che sia installata di R o Python oppure entrambi. Selezionare questo account per solo l'istanza predefinita.
    + Se si usa un' _istanza denominata_, il nome dell'istanza viene aggiunto al nome del nome del gruppo ruolo di lavoro predefinito, `SQLRUserGroup`. Di conseguenza, se l'istanza è denominata "MLTEST", il nome di gruppo utente predefinito per questa istanza sarebbe **SQLRUserGroupMLTest**.
 
     ![Esempio di gruppi nel server](media/implied-auth-login5.png "esempio di gruppi sul server")
   
5. Fare clic su **OK** per chiudere la finestra di dialogo di ricerca avanzata.

    > [!IMPORTANT]
    > Assicurarsi di che aver selezionato l'account corretto per l'istanza. Ogni istanza può usare solo il proprio servizio Launchpad e il gruppo creato per tale servizio. Le istanze non possono condividere un account di servizio o di lavoro di Launchpad.

6. Fare clic su **OK** ancora una volta per chiudere la **Seleziona utente o gruppo** nella finestra di dialogo.

7. Nel **account di accesso - nuovo** finestra di dialogo, fare clic su **OK**. Per impostazione predefinita, l'account di accesso viene assegnato al ruolo **public** e dispone dell'autorizzazione per connettersi al motore di database.