---
title: 'Esercitazione: Abilitare il widget dello spazio utilizzato per le tabelle in SQL Operations Studio (anteprima) | Microsoft Docs'
description: Con questa esercitazione viene illustrato come abilitare il widget dello spazio utilizzato per le tabelle sulla dashboard del database in SQL Operations Studio (anteprima).
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
ms.openlocfilehash: 7c51c7d1804baa490e665d316a08d911038c9f11
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Esercitazione: Abilitare il widget dello spazio utilizzato per le tabelle su [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Con questa esercitazione viene illustrato come abilitare un widget sulla dashboard del database al fine di avere una panoramica sull'utilizzo dello spazio per tutte le tabelle in un database. Durante questa esercitazione, si apprenderà come:

> [!div class="checklist"]
> * Attivare rapidamente un widget insight utilizzando un esempio incorporato
> * Visualizzare i dettagli sullo spazio utilizzato dalle tabelle
> * Filtrare i dati e visualizzare i dettagli sul grafico nel widget

## <a name="prerequisites"></a>Prerequisiti

Questa esercitazione richiede il database *TutorialDB* su SQL Server o Database SQL di Azure. Per crearlo, completare una delle guide rapide seguenti:

- [Connettersi ed eseguire query su SQL Server con tramite [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query sul Database SQL di Azure tramite [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Attivare un widget insight sulla dashboard del database su [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] offre un widget incorporato per monitorare lo spazio utilizzato dalle tabelle in un database.

1. Al fine di accedere al file delle **IMPOSTAZIONI UTENTE** premere **Ctrl+MAIUSC+P** per aprire il *riquadro comandi*. Scrivere *impostazioni* nella casella di ricerca e dai file di impostazioni disponibili, selezionare **Preferenze: Apri impostazioni utente**.

   ![Comando apri impostazioni utente](./media/tutorial-qds-sql-server/open-user-settings.png)

2. Scrivere ora *dashboard* nella ricerca impostazioni e individuare **dashboard.database.widgets**.

   ![Impostazioni di ricerca](./media/tutorial-qds-sql-server/search-settings.png)

3. Come mostrato nell'immagine precedente, lo schermo è diviso in due parti, una per le **IMPOSTAZIONI PREDEFINITE** e una per le **IMPOSTAZIONI UTENTE**, Per personalizzare l'impostazione **dashboard.database.widgets** premere col mouse l'icona con la matita a sinistra del testo **dashboard.database.widgets** nell'area **IMPOSTAZIONI PREDEFINITE** e fare clic su **Modifica**>**Copia nelle impostazioni**. L'operazione copierà l'intera impostazione dalle **IMPOSTAZIONI PREDEFINITE** alle **IMPOSTAZIONI UTENTE**. Attenzione, se l'impostazione è già stata precedentemente aggiunta, non scegliere di copiare il contenuto e procedere al punto successivo, aggiungendo a mano la parte mancante.
Per personalizzare il **dashboard.database.widgets** impostazione mouse sull'icona della matita a sinistra del **dashboard.database.widgets** testo, fare clic su **modifica**>**Copia impostazioni**.

4. Utilizzando [!INCLUDE[name-sos](../includes/name-sos-short.md)] aggiungere il widget come segue:
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
Configurare le impostazioni tramite IntelliSense, indicando nella proprietà *name* il titolo del widget, in *gridItemConfig* la dimensione e in *widget* aggiungere **table-space-db-insight**. Il risultato dovrebbe essere simile al seguente:

   ![Impostazioni di analisi](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. Premere **Ctrl+S** per salvare le impostazioni.

6. Aprire la dashboard del database con il tasto destro del mouse su **TutorialDB**>**Gestisci**.

   ![Aprire dashboard](./media/tutorial-table-space-sql-server/insight-open-dashboard.png)

7. Ecco come appare il widget *utilizzo dello spazio delle tabelle*:

   ![Widget](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Utilizzare il grafido del widget insight

Il grafigo insight di [!INCLUDE[name-sos](../includes/name-sos-short.md)] fornisce filtri e dettagli al passaggio del mouse. Provare i passaggi seguenti:

1. Fare click con il mouse sull'etichetta *rows_count* nella legenda del grafico. [!INCLUDE[name-sos](../includes/name-sos-short.md)] riadatta il grafico in base a quali etichette sono state selezionate.
    
2. Passare il puntatore del mouse sul grafico. [!INCLUDE[name-sos](../includes/name-sos-short.md)] mostra ulteriori informazioni sulla serie di dati e il relativo valore, come illustrato nella schermata seguente:

   ![legenda e attiva/disattiva grafico](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>Passaggi successivi
In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Attivare rapidamente un widget insight utilizzando un esempio incorporato
> * Visualizzare i dettagli sullo spazio utilizzato dalle tabelle
> * Filtrare i dati e visualizzare i dettagli sul grafico nel widget

Per informazioni su come costruire un widget insight personalizzato, completare l'esercitazione successiva:

> [!div class="nextstepaction"]
> [Costruire un widget insight personalizzato](tutorial-build-custom-insight-sql-server.md).
