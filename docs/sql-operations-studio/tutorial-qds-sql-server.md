---
title: "Esercitazione: Esempio di query più lente Abilita i cinque widget - Studio operazioni SQL (anteprima) | Documenti Microsoft"
description: "Questa esercitazione viene illustrato come abilitare il widget di esempio le query più lente cinque nel dashboard del database."
ms.custom: tools|sos
ms.date: 11/16/2017
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
ms.openlocfilehash: fc30051dff2bef07ac3e7d06aa98d92d4e05e79e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>Esercitazione: Aggiunta di *cinque query più lente* widget di esempio per il dashboard del database

Questa esercitazione viene illustrato il processo di aggiunta di uno dei [!INCLUDE[name-sos](../includes/name-sos-short.md)]del widget esempio incorporata per il *dashboard del database* per visualizzare rapidamente i cinque query più lente del database. Inoltre illustrato come visualizzare i dettagli delle query lente e piani di query utilizzando [!INCLUDE[name-sos](../includes/name-sos-short.md)]della funzionalità. Durante questa esercitazione, si apprenderà come:

> [!div class="checklist"]
> * Abilitare l'archivio Query in un database
> * Aggiungere un widget insight preesistente al dashboard di database
> * Visualizzare i dettagli sulle query più lente del database
> * Consente di visualizzare piani di esecuzione di query per le query più lente

[!INCLUDE[name-sos](../includes/name-sos-short.md)]include diverse informazioni widget out-of-the-box. In questa esercitazione viene illustrato come aggiungere il *-dati-archivio-db-informazioni dettagliate query* widget, ma i passaggi sono fondamentalmente lo stesso per l'aggiunta di un widget.

## <a name="prerequisites"></a>Prerequisites

Questa esercitazione richiede SQL Server o Database SQL di Azure *TutorialDB*. Per creare il *TutorialDB* del database, completare una delle Guide rapide seguenti:

- [Connettersi ed eseguire query tramite SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query utilizzando il Database SQL di Azure[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>Attivare l'archivio Query per il database

Il widget in questo esempio richiede *archivio Query* sia abilitato quindi eseguire l'istruzione Transact-SQL (T-SQL) seguente nel database:

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-an-insight-widget-to-your-database-dashboard"></a>Aggiungere un widget insight al Dashboard di Database

Per aggiungere un widget insight al dashboard, modificare il *dashboard.database.widgets* impostazione il *impostazioni utente* file.

1. Aprire *impostazioni utente* premendo **Ctrl + MAIUSC + P** per aprire la *comando tavolozza*.
2. Tipo *impostazioni* nella casella di ricerca e dai file di impostazioni disponibili, selezionare **preferenze: aprire le impostazioni utente**.

   ![Comando impostazioni utente aperte](./media/tutorial-qds-sql-server/open-user-settings.png)

2. Tipo *dashboard* nella ricerca impostazioni e individuare **dashboard.database.widgets**.

   ![Impostazioni di ricerca](./media/tutorial-qds-sql-server/search-settings.png)

3. Per personalizzare il **dashboard.database.widgets** impostazione mouse sull'icona della matita a sinistra del **dashboard.database.widgets** testo, fare clic su **modifica**  >  **Copia impostazioni**.

4. Dopo aver copiato le impostazioni per **dashboard.database.widgets**, posizionare il cursore alla fine della riga dopo la parentesi quadra aperta, premere **invio**e aggiungere una parentesi graffa simile al seguente (parentesi graffa di chiusura verranno visualizzati automaticamente):

   ```json
   "dashboard.database.widgets": [
   {}
   ```
5. Con il cursore all'interno di parentesi graffe, premere **Ctrl + barra spaziatrice** e selezionare **nome**. 
6. Completare la configurazione del widget in modo che rispecchi simile al seguente:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "slow queries widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "query-data-store-db-insight": null
            }
        }
    ...
    ```

5. Premere **Ctrl + S** per salvare la modifica **impostazioni utente**.

6. Aprire il *dashboard del Database* passando a **TutorialDB** nel *server* barra laterale, pulsante destro del mouse e scegliere **Gestisci**.

   ![Aprire dashboard](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Il widget insight viene visualizzato nel dashboard: 

   ![Widget QDS](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>Visualizzare i dettagli delle informazioni per ulteriori informazioni

1. Per visualizzare informazioni aggiuntive per un widget di informazioni dettagliate, fare clic sui puntini di sospensione (**...** ) in alto a destra e seleziona **Mostra dettagli**.
2. Per visualizzare ulteriori dettagli per un elemento, selezionare un elemento nel **dati grafico** elenco.

   ![Finestra di dialogo Dettagli Insight](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. Fare doppio clic su **query_sql_txt** in **dettagli elemento** e fare clic su **Copia cella**.

4. Chiudi il **Insights** riquadro.

## <a name="view-the-query-plan"></a>Visualizzare il piano di query 

1. Aprire un nuovo editor di query premendo **Ctrl + N**.

2. Incollare il testo della query nei passaggi precedenti nell'editor.

3. Fare clic su **spiegare**.

   ![Informazioni dettagliate QDS spiegare](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. Visualizzare il piano di esecuzione della query:

   ![showplan](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>Salvare e aprire un piano di query 

1. Aprire la finestra di dialogo Dettagli informazioni dettagliate.
2. Selezionare uno degli elementi di query.
2. Fare doppio clic su **query_plan** valore e selezionare **Copia cella**

   ![Approfondimenti QDS piano](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. Premere **Ctrl + N** per aprire un nuovo editor.

4. Incollare il piano copiato nell'editor.

5. Premere **Ctrl + S** per salvare il file e modificare l'estensione del file *sqlplan*. Per questa esercitazione, denominare il file *slowquery.sqlplan*.

6. Il piano di query viene aperta in [!INCLUDE[name-sos](../includes/name-sos-short.md)]del Visualizzatore di piano di query:

   ![Approfondimenti QDS piano](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>Passaggi successivi
In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Abilitare l'archivio Query in un database
> * Aggiungere un widget di informazioni dettagliate per il dashboard del database
> * Visualizzare i dettagli sulle query più lente del database
> * Consente di visualizzare piani di esecuzione di query per le query più lente


Per informazioni su come abilitare il **utilizzo dello spazio di tabella** esempio informazioni dettagliate, completare l'esercitazione successiva:

> [!div class="nextstepaction"]
> [Abilitare il widget di tabella spazio esempio informazioni dettagliate](tutorial-table-space-sql-server.md)