---
title: 'Esercitazione: Creare un widget di informazioni personalizzate in Studio operazioni SQL (anteprima) | Documenti Microsoft'
description: In questa esercitazione viene illustrato come compilare widget insight personalizzati e aggiungerli al dashboard di server e database in Studio operazioni SQL (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
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
ms.openlocfilehash: 344cf021a4a0abc13fc8c531875c604095c8c0d1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-build-a-custom-insight-widget"></a>Esercitazione: Creare un widget di informazioni personalizzate

Questa esercitazione viene illustrato come utilizzare le query di analisi per compilare widget personalizzati informazioni dettagliate.

Durante questa esercitazione si apprenderà come:
> [!div class="checklist"]
> * Eseguire una query e visualizzarlo in un grafico
> * Compilare un widget di informazioni personalizzate dal grafico
> * Aggiungere il grafico a un dashboard di server o database
> * Aggiungere i dettagli per il widget di informazioni personalizzate

## <a name="prerequisites"></a>Prerequisites

Questa esercitazione richiede SQL Server o Database SQL di Azure *TutorialDB*. Per creare il *TutorialDB* del database, completare una delle Guide rapide seguenti:

- [Connettersi ed eseguire query tramite SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query utilizzando il Database SQL di Azure[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>Eseguire una query e visualizzare il risultato in una visualizzazione grafico
In questo passaggio, eseguire uno script sql per eseguire la query corrente sessioni attive.

1. Per aprire un nuovo editor, premere **Ctrl + N**. 

2. Modificare il contesto di connessione per **TutorialDB**.

3. Incollare la query seguente nell'editor di query:

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. Salvare la query nell'editor per un \*file con estensione SQL. Per questa esercitazione, salvare lo script come *activeSession.sql*.

5. Per eseguire la query, premere **F5**.

6. Dopo che vengono visualizzati i risultati della query, fare clic su **visualizzazione sotto forma di grafico**, quindi fare clic su di **Visualizzatore grafico** scheda.

7. Modifica **tipo di grafico** a **conteggio**. Queste impostazioni il rendering di un grafico di conteggio.

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>Aggiungere le informazioni personalizzate al dashboard di database

1. Per aprire la configurazione del widget informazioni dettagliate, fare clic su **creare Insight** su *Visualizzatore grafico*:

   ![configurazione](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. Copiare la configurazione di analisi (i dati JSON). 

3. Premere **Ctrl + virgola** per aprire *impostazioni utente*.

4. Tipo *dashboard* in *le impostazioni di ricerca*.

5. Fare clic su **modifica** per *dashboard.database.widgets*.

   ![Impostazioni del dashboard](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. Incollare la configurazione di una visione JSON in *dashboard.database.widgets*. Database dashboard impostazioni ha un aspetto simile al seguente:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql"
                }
            }
        }
    ]
   ```

7. Salvare il *impostazioni utente* file e aprire il *TutorialDB* dashboard per visualizzare il widget di sessioni attive del database:

   ![informazioni dettagliate activesession](./media/tutorial-build-custom-insight-sql-server/insight-activesession-dashboard.png)

## <a name="add-details-to-custom-insight"></a>Aggiungere i dettagli per informazioni dettagliate personalizzato

1. Per aprire un nuovo editor, premere **Ctrl + N**.

2. Modificare il contesto di connessione per **TutorialDB**.

3. Incollare la query seguente nell'editor di query:

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. Salvare la query nell'editor per un \*file con estensione SQL. Per questa esercitazione, salvare lo script come *activeSessionDetail.sql*.

5. Premere **Ctrl + virgola** per aprire *impostazioni utente*.

6. Modifica esistente *dashboard.database.widgets* nodo nel file di impostazioni:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql",
                    "details": {
                        "queryFile": "{your file folder}/activeSessionDetail.sql",
                        "label": "SID",
                        "value": "Login Name"
                    }
                }
            }
        }
    ]
   ```

7. Salvare il *impostazioni utente* file e aprire il *TutorialDB* dashboard del database. Fare clic sul pulsante con i puntini di sospensione (...) accanto a *My Widget* per visualizzare i dettagli:

    ![informazioni dettagliate activesession](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>Passaggi successivi
In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Eseguire una query e visualizzarlo in un grafico
> * Compilare un widget di informazioni personalizzate dal grafico
> * Aggiungere il grafico a un dashboard di server o database
> * Aggiungere i dettagli per il widget di informazioni personalizzate

Per informazioni su come eseguire il backup e ripristino di database, completare l'esercitazione successiva:

> [!div class="nextstepaction"]
> [Eseguire il backup e ripristino di database](tutorial-backup-restore-sql-server.md).