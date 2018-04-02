---
title: "Esercitazione: Aggiungere il widget delle cinque query più lente - SQL Operations Studio (anteprima) | Microsoft Docs"
description: "Con questa esercitazione viene illustrato come abilitare il widget delle cinque query più lente nella dashboard del database."
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

Con questa esercitazione viene illustrato il processo di aggiunta di uno dei widget incorporati in [!INCLUDE[name-sos](../includes/name-sos-short.md)] per la *dashboard del database* al fine di visualizzare rapidamente le cinque query più lente del database. Inoltre, viene mostrato come visualizzare i dettagli delle query lente e piani di query utilizzando le funzionalità di [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Durante questa esercitazione, si apprenderà come:

> [!div class="checklist"]
> * Abilitare Archivio Query in un database
> * Aggiungere un widget insight integrato al dashboard del database
> * Visualizzare i dettagli sulle query più lente del database
> * Visualizzare piani di esecuzione di query

[!INCLUDE[name-sos](../includes/name-sos-short.md)] include diversi widget insight integrati. In questa esercitazione viene illustrato come aggiungere il widget *query-data-store-db-insight*, ma i passaggi sono fondamentalmente gli stessi per l'aggiunta di altri widget.

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione richiede il database *TutorialDB*, su SQL Server o Database SQL di Azure. Per crearlo, completare una delle guide rapide seguenti:

- [Connettersi ed eseguire query su SQL Server tramite [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query sul Database SQL di Azure tramite [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>Attivare Archivio Query per il database

Il widget in questo esempio richiede *Archivio Query* abilitato quindi eseguire l'istruzione Transact-SQL (T-SQL) seguente nel database:

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-an-insight-widget-to-your-database-dashboard"></a>Aggiungere il widget insight alla Dashboard del Database

Per aggiungere un widget insight alla dashboard, modificare l'impostazione *dashboard.database.widgets* nel file delle *impostazioni utente*.

1. Al fine di accedere al file delle **IMPOSTAZIONI UTENTE** premere **Ctrl+MAIUSC+P** per aprire il *riquadro comandi*.
2. Scrivere *impostazioni* nella casella di ricerca e dai file di impostazioni disponibili, selezionare **Preferenze: Apri impostazioni utente**.

   ![Comando apri impostazioni utente](./media/tutorial-qds-sql-server/open-user-settings.png)

3. Scrivere ora *dashboard* nella ricerca impostazioni e individuare **dashboard.database.widgets**.

   ![Impostazioni di ricerca](./media/tutorial-qds-sql-server/search-settings.png)

4. Come mostrato nell'immagine precedente, lo schermo è diviso in due parti, una per le **IMPOSTAZIONI PREDEFINITE** e una per le **IMPOSTAZIONI UTENTE**, Per personalizzare l'impostazione **dashboard.database.widgets** premere col mouse l'icona con la matita a sinistra del testo **dashboard.database.widgets** nell'area **IMPOSTAZIONI PREDEFINITE** e fare clic su **Modifica**>**Copia nelle impostazioni**. L'operazione copierà l'intera impostazione dalle **IMPOSTAZIONI PREDEFINITE** alle **IMPOSTAZIONI UTENTE**. Attenzione, se l'impostazione è già stata precedentemente aggiunta, non scegliere di copiare il contenuto e procedere al punto successivo, aggiungendo a mano la parte mancante.

5. In **dashboard.database.widgets**, posizionare il cursore alla fine della riga dopo la parentesi quadra aperta, premere **invio**e e aggiungere una parentesi graffa aperta (la parentesi graffa di chiusura verrà aggiunta automaticamente):

   ```json
   "dashboard.database.widgets": [
   {}
   ```
6. Con il cursore all'interno di parentesi graffe, premere **Ctrl+barra spaziatrice** e selezionare **name**. Completare la configurazione del widget in modo che sia simile al seguente (potrebbero esistere altri widget, in tal caso separare ognuno di essi con una virgola:

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

7. Premere **Ctrl+S** per salvare la modifica sulle **IMPOSTAZIONI UTENTE**.

8. Tornare ora alla *dashboard del Database* selezionando **TutorialDB** nella barra laterale dei *SERVER*, premere il pulsante destro del mouse e scegliere **Gestisci**.

   ![Aprire dashboard](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

9. Il widget insight viene visualizzato come segue: 

   ![Widget QDS](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>Visualizzare i dettagli del widget insight per ulteriori informazioni

1. Per visualizzare informazioni aggiuntive di un widget insight, fare clic sui puntini di sospensione (**...** ) in alto a destra e seleziona **Mostra dettagli**.
2. Per visualizzare ulteriori dettagli di un elemento, selezionarlo dall'elenco dei **dati**.

   ![Finestra di dialogo Dettagli Insight](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. Premere il tasto destro sulla cella a fianco di **query_sql_txt** nel riquadro **dettagli elemento** e fare clic su **Copia cella**.

4. Chiudi il riquadro **Insights**.

## <a name="view-the-query-plan"></a>Visualizzare il piano di query 

1. Aprire un nuovo editor di query premendo **Ctrl+N**.

2. Incollare il testo della query copiato nei passaggi precedenti.

3. Fare clic su **mostra il piano**.

   ![Informazioni dettagliate QDS](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. Visualizzare il piano di esecuzione della query:

   ![showplan](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>Salvare e aprire un piano di query 

1. Aprire la finestra dei dettagli del widget insight.
2. Selezionare uno degli elementi tra i dati.
3. Premere il tasto destro sulla cella a fianco di **query_plan** nel riquadro **dettagli elemento** e fare clic su **Copia cella**

   ![Approfondimenti QDS piano](./media/tutorial-qds-sql-server/insight-qds-plan.png)

4. Premere **Ctrl+N** per aprire un nuovo editor.

5. Incollare il piano copiato nell'editor.

6. Premere **Ctrl+S** per salvare il file e modificare l'estensione del file in *.sqlplan*. Per questa esercitazione, denominare il file *slowquery.sqlplan*. Se l'estensione non appare nella lista dei tipi per cui effettuare il salvataggio, scriverla manualmente.

7. Il piano di query viene aperto in [!INCLUDE[name-sos](../includes/name-sos-short.md)] e mostrata tramite il Visualizzatore dei piani di query:

   ![Approfondimenti QDS piano](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>Passaggi successivi
In questa esercitazione si è appreso come:
> [!div class="checklist"]
> * Abilitare Archivio Query in un database
> * Aggiungere un widget insight integrato al dashboard del database
> * Visualizzare i dettagli sulle query più lente del database
> * Visualizzare piani di esecuzione di query


Per informazioni su come abilitare il widget di **spazio utilizzato per le tabelle**, completare l'esercitazione successiva:

> [!div class="nextstepaction"]
> [Abilitare il widget insight di spazio utilizzato per le tabelle](tutorial-table-space-sql-server.md)
