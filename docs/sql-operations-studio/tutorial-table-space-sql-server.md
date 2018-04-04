---
title: 'Esercitazione: Abilitare il widget tabella spazio utilizzo esempio informazioni dettagliate in Studio operazioni SQL (anteprima) | Documenti Microsoft'
description: Questa esercitazione viene illustrato come abilitare il widget tabella spazio utilizzo esempio informazioni dettagliate sul dashboard del database di Studio operazioni SQL (anteprima).
ms.custom: tools|sos
ms.date: 03/19/2018
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 09a1ebe6fda1baf546923887f28b51d416a80b59
ms.sourcegitcommit: 6bd21109abedf64445bdb3478eea5aaa7553fa46
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2018
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Esercitazione: Abilitare la tabella spazio utilizzo esempio insight widget usare [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Questa esercitazione viene illustrato come abilitare un widget di informazioni nel dashboard di database, fornendo una visualizzazione in panoramica sull'utilizzo dello spazio per tutte le tabelle in un database. Durante questa esercitazione, si apprenderà come:

> [!div class="checklist"]
> * Attivare rapidamente un widget insight utilizzando un esempio di widget insight incorporato
> * Visualizzare i dettagli di utilizzo dello spazio di tabella
> * Filtrare i dati e visualizzare i dettagli di etichetta su un grafico di informazioni dettagliate

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione richiede SQL Server o Database SQL di Azure *TutorialDB*. Per creare il *TutorialDB* del database, completare una delle Guide rapide seguenti:

- [Connettersi ed eseguire query tramite SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query utilizzando il Database SQL di Azure [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Attivare una visione gestione [!INCLUDE[name-sos](../includes/name-sos-short.md)]del dashboard del database
[!INCLUDE[name-sos](../includes/name-sos-short.md)] ha un widget di esempio incorporata per monitorare lo spazio utilizzato dalle tabelle in un database.

1. Aprire *impostazioni utente* premendo **Ctrl + MAIUSC + P** per aprire la *comando tavolozza*.
2. Tipo di *impostazioni* nella casella di ricerca e selezionare **preferenze: aprire le impostazioni utente**.
2. Tipo *dashboard* casella di input per le impostazioni di ricerca e individuare **dashboard.database.widgets**.

3. Per personalizzare il **dashboard.database.widgets** impostazioni è necessario modificare il **dashboard.database.widgets** voce il **impostazioni utente** sezione (la colonna nel lato destro). Se è presente alcun **dashboard.database.widgets** nel **le impostazioni utente** sezione, passare il mouse sul **dashboard.database.widgets** testo nella colonna impostazioni predefinite e fare clic su l'icona a forma di matita visualizzata a sinistra del testo e fare clic su **copia alle impostazioni**. Se viene visualizzato il messaggio popup **sostituire nelle impostazioni**, selezionarla. Passare ai **delle impostazioni utente** colonna a destra e individuare il **dashboard.database.widgets** sezione e passare alla sezione successiva.

4. Nel **dashboard.database.widgets** sezione, aggiungere le seguenti:

   ```json
        {
            "name": "Space Used by Tables",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "table-space-db-insight": null
            }
        },
    ```
Il **dashboard.database.widgets** sezione dovrebbe essere simile all'immagine seguente:

   ![Impostazioni di ricerca](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. Premere **Ctrl + S** per salvare le impostazioni.

6. Dashboard del database aperta facendo clic **TutorialDB** e fare clic su **Gestisci**.

7. Visualizza il *spazio tabelle* widget informazioni dettagliate, come illustrato nella figura seguente: 

   ![Widget](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Utilizzo con il grafico di informazioni dettagliate

[!INCLUDE[name-sos](../includes/name-sos-short.md)]del grafico di informazioni dettagliate vengono fornite informazioni dettagliate di filtro e di passaggio del mouse. Per provare i passaggi seguenti:

1. Fare clic su e attivare o disattivare il *row_count* sulla legenda del grafico. [!INCLUDE[name-sos](../includes/name-sos-short.md)] Mostra e nasconde serie di dati come una legenda attivare o disattivare.
    
2. Passare il puntatore del mouse sul grafico. [!INCLUDE[name-sos](../includes/name-sos-short.md)] Visualizza ulteriori informazioni sull'etichetta della serie di dati e il relativo valore come illustrato nella schermata seguente.

   ![legenda e attiva/disattiva grafico](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>Passaggi successivi
In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Attivare rapidamente un widget insight utilizzando un campione del widget insight incorporato.
> * Visualizzare i dettagli di utilizzo dello spazio di tabella.
> * Filtrare i dati e visualizzare i dettagli di etichetta su un grafico di informazioni dettagliate

Per informazioni su come compilare un widget di informazioni personalizzate, completare l'esercitazione successiva:

> [!div class="nextstepaction"]
> [Compilare un widget personalizzati insight](tutorial-build-custom-insight-sql-server.md).