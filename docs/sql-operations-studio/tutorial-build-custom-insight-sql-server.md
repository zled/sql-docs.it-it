---
title: 'Esercitazione: Creare un widget di informazioni dettagliate personalizzato in SQL Operations Studio (preview) | Microsoft Docs'
description: Con questa esercitazione viene mostrato come costruire un widget di informazioni dettagliate personalizzato e come aggiungerlo al dashboard di server e database in SQL Operations Studio (preview).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
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
# <a name="tutorial-build-a-custom-insight-widget"></a>Esercitazione: Creare un widget di informazioni dettagliate personalizzato

Con questa esercitazione viene mostrato come costruire un widget di informazioni dettagliate personalizzato sfruttando le query di informazioni dettagliate.

Durante questa esercitazione si apprenderà come:
> [!div class="checklist"]
> * Eseguire una query e visualizzarla in un grafico
> * Compilare un widget di informazioni personalizzato dal grafico
> * Aggiungere il grafico a un dashboard di server o database
> * Aggiungere i dettagli per il widget di informazioni personalizzato.

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione richiede il database *TutorialDB* su SQL Server o Azure SQL Database. Per crearlo, completare una delle guide rapide seguenti:

- [Connettersi ed eseguire query su SQL Server tramite[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query su Azure SQL Database tramite[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>Eseguire una query e visualizzare il risultato in un grafico
In questo passaggio, eseguiremo uno script sql per ottenere la lista delle sessioni attive.

1. Per aprire un nuovo editor, premere **Ctrl + N**. 

2. Modificare il contesto di connessione su **TutorialDB**.

3. Incollare la query seguente nell'editor di query:

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. Salvare la query in un \*file con estensione `.sql`. Per questa esercitazione, salvare lo script come *activeSession.sql*.

5. Per eseguire la query, premere **F5**.

6. Dopo che vengono visualizzati i risultati della query, fare clic su **Visualizzazione grafico** nella barra laterale a destra dei risultati, quindi fare clic sulla scheda **Visualizzatore grafico**.

7. Modifica **tipo di grafico** a **conteggio**. Queste impostazioni il rendering di un grafico di conteggio.

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>Aggiungere le informazioni dettagliate personalizzate alla dashboard del database

1. Per aprire la configurazione del widget di informazioni dettagliate, fare clic su **creare informazioni dettagliate** nel *Visualizzatore grafico*:

   ![configurazione](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. Copiare la configurazione proposta (il JSON).  

3. Premere **Ctrl+virgola** per aprire le *impostazioni utente*.

4. Scrivere *dashboard* in *Cerca impostazioni*.

5. Fare clic su **modifica** per *dashboard.database.widgets*.

   ![Impostazioni del dashboard](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. Incollare il frammento di JSON in *dashboard.database.widgets*. Le impostazioni della dashboard del database dovrebbero essere simili al seguente listato:

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

7. Salvare le *impostazioni utente* e aprire la dashboard del database *TutorialDB* per visualizzare il widget con le sessioni attive:

   ![insight activesession](./media/tutorial-build-custom-insight-sql-server/insight-activesession-dashboard.png)

## <a name="add-details-to-custom-insight"></a>Aggiungere i dettagli al widget personalizzato

1. Per aprire un nuovo editor, premere **Ctrl + N**.

2. Modificare il contesto di connessione su **TutorialDB**.

3. Incollare la query seguente nell'editor di query:

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. Salvare la query in un \*file con estensione `.sql`. Per questa esercitazione, salvare lo script come *activeSessionDetail.sql*.

5. Premere **Ctrl+virgola** per aprire le *impostazioni utente*.

6. Modificare il nodo *dashboard.database.widgets* nel file di impostazioni:

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

7. Salvare le *impostazioni utente* e aprire la dashboard di *TutorialDB*. Fare clic sul pulsante con i puntini di sospensione (...) accanto a *My Widget* per visualizzare i dettagli:

    ![insight activesession](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>Passaggi successivi
In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Eseguire una query e visualizzarla in un grafico
> * Compilare un widget di informazioni personalizzato dal grafico
> * Aggiungere il grafico a un dashboard di server o database
> * Aggiungere i dettagli per il widget di informazioni personalizzato.

Per informazioni su come eseguire backup e ripristino di database, completare l'esercitazione successiva:

> [!div class="nextstepaction"]
> [Eseguire backup e ripristino di database](tutorial-backup-restore-sql-server.md).