---
title: 'Esercitazione: Abilitare il widget tabella spazio utilizzo esempio informazioni dettagliate in Studio operazioni SQL (anteprima) | Documenti Microsoft'
description: Questa esercitazione viene illustrato come abilitare il widget tabella spazio utilizzo esempio informazioni dettagliate sul dashboard del database di Studio operazioni SQL (anteprima).
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
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Esercitazione: Abilitare la tabella spazio utilizzo esempio insight widget utilizzando[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Questa esercitazione viene illustrato come abilitare un widget di informazioni nel dashboard di database, fornendo una visualizzazione in panoramica sull'utilizzo dello spazio per tutte le tabelle in un database. Durante questa esercitazione, si apprenderà come:

> [!div class="checklist"]
> * Attivare rapidamente un widget insight utilizzando un esempio di widget insight incorporato
> * Visualizzare i dettagli di utilizzo dello spazio di tabella
> * Filtrare i dati e visualizzare i dettagli di etichetta su un grafico di informazioni dettagliate

## <a name="prerequisites"></a>Prerequisites

Questa esercitazione richiede SQL Server o Database SQL di Azure *TutorialDB*. Per creare il *TutorialDB* del database, completare una delle Guide rapide seguenti:

- [Connettersi ed eseguire query tramite SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Connettersi ed eseguire query utilizzando il Database SQL di Azure[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Attivare una visione gestione [!INCLUDE[name-sos](../includes/name-sos-short.md)]del dashboard del database
[!INCLUDE[name-sos](../includes/name-sos-short.md)]è un widget di esempio incorporata per monitorare lo spazio utilizzato dalle tabelle in un database.

1. Aprire **impostazioni utente** premendo **Ctrl + MAIUSC + P** per aprire *comando tavolozza*, tipo *impostazioni* nella casella di ricerca e selezionare  **Preferenze: Aprire le impostazioni utente**.

   ![Comando impostazioni utente aperte](./media/tutorial-table-space-sql-server/open-user-settings.png)

2. Tipo *dashboard* casella di input per le impostazioni di ricerca e individuare **dashboard.database.widgets**.

   ![Impostazioni di ricerca](./media/tutorial-table-space-sql-server/search-settings.png)

3. Per personalizzare il **dashboard.database.widgets** impostazione mouse sull'icona della matita a sinistra del **dashboard.database.widgets** testo, fare clic su **modifica**  >  **Copia impostazioni**.

4. Utilizzando [!INCLUDE[name-sos](../includes/name-sos-short.md)]di configurare le impostazioni delle informazioni IntelliSense, *nome* per il titolo del widget, *gridItemConfig* per la dimensione, widget e *widget* selezionando **insight-tabella-spazio-db** dall'elenco a discesa come illustrato nella schermata seguente:

   ![Impostazioni di analisi](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. Premere **Ctrl + S** per salvare le impostazioni.

6. Dashboard del database aperta facendo clic **TutorialDB** e fare clic su **Gestisci**.

   ![Aprire dashboard](./media/tutorial-table-space-sql-server/insight-open-dashboard.png)

7. Visualizzazione *spazio utilizzato dalle tabelle* come illustrato nella schermata seguente: 

   ![Widget](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Utilizzo con il grafico di informazioni dettagliate

[!INCLUDE[name-sos](../includes/name-sos-short.md)]del grafico insight fornisce i dettagli di filtro e di passaggio del mouse. Per provare i passaggi seguenti:

1. Fare clic su e attivare o disattivare il *row_count* sulla legenda del grafico. [!INCLUDE[name-sos](../includes/name-sos-short.md)]Mostra e nasconde serie di dati come si attiva una legenda o disattiva.
    
2. Passare il puntatore del mouse sul grafico. [!INCLUDE[name-sos](../includes/name-sos-short.md)]Mostra ulteriori informazioni sull'etichetta della serie di dati e il relativo valore, come illustrato nella schermata seguente.

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