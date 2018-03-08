---
title: 'Lezione dell''esercitazione di Analysis Services 10: creare partizioni | Documenti Microsoft'
description: Viene descritto come creare partizioni del progetto di Analysis Services tutorial.
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: 
author: Minewiskan
manager: kfile
editor: 
tags: 
ms.assetid: 
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
ms.openlocfilehash: 417bcbe36a49c44bcb5c8297968e6595d1ed3d91
ms.sourcegitcommit: 7ed8c61fb54e3963e451bfb7f80c6a3899d93322
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2018
---
# <a name="create-partitions"></a>Creare partizioni

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In questa lezione è creare partizioni per dividere la tabella FactInternetSales in parti logiche più piccole che possono essere elaborate (aggiornate) indipendentemente dalle altre. Per impostazione predefinita, ogni tabella che inclusa nel modello dispone di una partizione, che include colonne e righe della tabella. Per la tabella FactInternetSales, di voler dividere i dati per anno. una partizione per ognuno dei cinque anni della tabella. Ogni partizione può quindi essere elaborata in modo indipendente. Per ulteriori informazioni, vedere [partizioni](../tabular-models/partitions-ssas-tabular.md). 
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

In questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 9: creare gerarchie](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Creare partizioni  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>Per creare partizioni nella tabella FactInternetSales  
  
1.  In Esplora modelli tabulari, espandere **tabelle**e quindi fare doppio clic su **FactInternetSales** > **partizioni**.  
  
2.  In Gestione partizioni, fare clic su **copia**e quindi modificare il nome in **FactInternetSales2010**.
  
    Dal momento che la partizione includa solo le righe all'interno di un determinato periodo, per l'anno 2010, è necessario modificare l'espressione di query.
  
4.  Fare clic su **progettazione** per aprire l'Editor di Query e quindi fare clic su di **FactInternetSales2010** query.

5.  Nell'anteprima, fare clic sulla freccia rivolta verso il basso il **OrderDate** intestazione di colonna e quindi fare clic su **filtri data/ora** > **tra**.

    ![as-lesson10-query-editor](../tutorial-tabular-1400/media/as-lesson10-query-editor.png)

6.  Nella finestra di dialogo Filtra righe in **Mostra righe in cui: OrderDate**, lasciare **è dopo o uguale a**, quindi immettere nel campo Data **1/1/2010**. Lasciare il **e** operatore selezionato, quindi selezionare **prima**, quindi immettere nel campo Data, **1/1/2011**e quindi fare clic su **OK**.

    ![as-lesson10-filter-rows](../tutorial-tabular-1400/media/as-lesson10-filter-rows.png)
    
    Si noti nell'Editor di Query in passaggi applicati, viene visualizzato un altro passaggio denominato righe filtrate. Questo filtro consiste nel selezionare solo le date degli ordini da 2010.

8.  Fare clic su **Importa**.

    In Gestione partizioni, rilevare l'espressione di query ora una clausola di filtrare le righe aggiuntiva.

    ![as-lesson10-query](../tutorial-tabular-1400/media/as-lesson10-query.png)
  
    Questa istruzione consente di specificare che la partizione deve includere solo i dati delle righe in cui OrderDate si nell'anno di calendario 2010 come specificato nella clausola righe filtrate.  
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>Per creare una partizione per l'anno 2011  
  
1.  Nell'elenco delle partizioni, fare clic su di **FactInternetSales2010** partizione creata e quindi fare clic su **copia**.  Modificare il nome di partizione in **FactInternetSales2011**. 

    Non è necessario utilizzare l'Editor di Query per creare una nuova clausola di righe filtrate. Poiché una copia della query è stato creato per 2010, è sufficiente è rendere una lieve modifica nella query per 2011.
  
2.  In **espressione di Query**, in ordine per la partizione includere solo le righe per l'anno 2011, sostituire gli anni nella clausola filtrate le righe con **2011** e **2012**, rispettivamente, ad esempio:  
  
    ```  
    let
        Source = #"SQL/localhost;AdventureWorksDW2014",
        dbo_FactInternetSales = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
        #"Removed Columns" = Table.RemoveColumns(dbo_FactInternetSales,{"OrderDateKey", "DueDateKey", "ShipDateKey"}),
        #"Filtered Rows" = Table.SelectRows(#"Removed Columns", each [OrderDate] >= #datetime(2011, 1, 1, 0, 0, 0) and [OrderDate] < #datetime(2012, 1, 1, 0, 0, 0))
    in
        #"Filtered Rows"
   
    ```  
  
#### <a name="to-create-partitions-for-2012-2013-and-2014"></a>Per creare partizioni per 2012, 2013 e 2014.  
  
- Seguire i passaggi precedenti, la creazione di partizioni per 2012, 2013 e 2014, la modifica di anni nella clausola filtrate le righe da includere solo le righe per tale anno. 
  

## <a name="delete-the-factinternetsales-partition"></a>Eliminare la partizione FactInternetSales

Dopo aver creato le partizioni per ogni anno, è possibile eliminare la partizione FactInternetSales; Quando si sceglie elabora tutte durante l'elaborazione di partizioni, impedendo si sovrappongono.

#### <a name="to-delete-the-factinternetsales-partition"></a>Per eliminare la partizione FactInternetSales

-  Fare clic su di **FactInternetSales** di partizione e quindi fare clic su **eliminare**.



## <a name="process-partitions"></a>Elaborare le partizioni  

In Gestione partizioni, si noti il **elaborati ultimo** colonna per ogni della nuova partizione creata mostra queste partizioni non sono mai state elaborate. Quando si creano partizioni, è consigliabile eseguire un'operazione di elaborazione delle partizioni o tabella di processo per aggiornare i dati nelle partizioni.  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>Per elaborare le partizioni FactInternetSales  
  
1.  Fare clic su **OK** per chiudere Gestione partizioni.  
  
2.  Fare clic sul **FactInternetSales** tabella, quindi scegliere il **modello** menu > **processo** > **elabora partizioni**.  
  
3.  Nella finestra di dialogo Elabora partizioni verificare **modalità** è impostato su **elaborazione predefinita**.  
  
4.  Selezionare la casella di controllo **Elabora** per ognuna delle cinque partizioni create, quindi fare clic su **OK**.  

    ![as-lesson10-process-partitions](../tutorial-tabular-1400/media/as-lesson10-process-partitions.png)
  
    Se viene chiesto di immettere le credenziali di rappresentazione, immettere il nome utente di Windows e la password specificati nella lezione 2.  
  
    Viene visualizzata la finestra di dialogo **Processo dati** , con informazioni dettagliate sul processo per ogni partizione. Si noti che per ogni partizione viene trasferito un numero diverso di righe. Ogni partizione include solo le righe per l'anno specificato nella clausola WHERE nell'istruzione SQL. Al termine dell'elaborazione, proseguire e chiudere la finestra di dialogo Processo dati.  
  
    ![as-lesson10-process-complete](../tutorial-tabular-1400/media/as-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>Quali sono le operazioni successive?

Passare alla lezione successiva: [lezione 11: creare ruoli](../tutorial-tabular-1400/as-lesson-11-create-roles.md). 
