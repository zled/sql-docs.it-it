---
title: Abilitare il widget dello spazio utilizzato per le tabelle in SQL Operations Studio (anteprima) | Microsoft Docs
description: Con questa esercitazione viene illustrato come abilitare il widget dello spazio utilizzato per le tabelle sulla dashboard del database in SQL Operations Studio (anteprima).
ms.custom: tools|sos
ms.date: 03/19/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a09dd273bb005432eaf638bb88c55ff35a5bd90
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235261"
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Esercitazione: Abilitare il widget dello spazio utilizzato per le tabelle su [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Con questa esercitazione viene illustrato come abilitare un widget sulla dashboard del database al fine di avere una panoramica sull'utilizzo dello spazio per tutte le tabelle in un database. Durante questa esercitazione, si apprenderà come:

> [!div class="checklist"]
> * Attivare rapidamente un widget di informazioni dettagliate utilizzando un esempio incorporato
> * Visualizzare i dettagli sullo spazio utilizzato dalle tabelle
> * Filtrare i dati e visualizzare il dettaglio dell'etichetta in un grafico di informazioni dettagliate

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione richiede *TutorialDB*, un database su SQL Server o Database SQL di Azure. Per crearlo, completare una delle guide rapide seguenti:

- [Connettersi ed eseguire query su SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query sul database SQL di Azure tramite [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Attivare una visione gestione [!INCLUDE[name-sos](../includes/name-sos-short.md)]del dashboard del database
[!INCLUDE[name-sos](../includes/name-sos-short.md)] offre un widget di esempio incorporato per monitorare lo spazio utilizzato dalle tabelle in un database.

1. Al fine di accedere al file delle *IMPOSTAZIONI UTENTE* premere **Ctrl+MAIUSC+P** per aprire il *riquadro comandi*.
2. Scrivere *impostazioni* nella casella di ricerca e dai file di impostazioni disponibili, selezionare **Preferenze: Apri impostazioni utente**.
2. Scrivere ora *dashboard* nella ricerca impostazioni e individuare **dashboard.database.widgets**.

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

6. Aprire la dashboard del database facendo clic con il pulsante destro del mouse su **TutorialDB**, quindi fare clic su **Gestisci**.

7. Visualizza il *spazio tabelle* widget informazioni dettagliate, come illustrato nella figura seguente: 

   ![Widget](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Utilizzo del grafico di informazioni dettagliate

Il grafico di informazioni dettagliate di [!INCLUDE[name-sos](../includes/name-sos-short.md)] fornisce filtri e dettagli al passaggio del mouse. Provare i passaggi seguenti:

1. Fare clic e attivare/disattivare la legenda *rows_count* nel grafico.  [!INCLUDE[name-sos](../includes/name-sos-short.md)] mostra e nasconde le serie di dati quando si attiva o disattiva una legenda.
    
2. Passare il puntatore del mouse sul grafico. [!INCLUDE[name-sos](../includes/name-sos-short.md)]mostra ulteriori informazioni sull'etichetta della serie di dati e il relativo valore, come illustrato nella schermata seguente:

   ![legenda e attiva/disattiva grafico](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>Passaggi successivi
In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Attivare rapidamente un widget di informazioni dettagliate utilizzando un esempio incorporato
> * Visualizzare i dettagli sullo spazio utilizzato dalle tabelle.
> * Filtrare i dati e visualizzare il dettaglio dell'etichetta in un grafico di informazioni dettagliate

Per informazioni su come costruire un widget di informazioni dettagliate personalizzato, completare l'esercitazione successiva:

> [!div class="nextstepaction"]
> [Costruire un widget di informazioni dettagliate personalizzato](tutorial-build-custom-insight-sql-server.md).