---
title: 'Lezione 11: Creare partizioni | Documenti Microsoft'
ms.custom: 
ms.date: 03/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57ed4f364bcc7ca144c6e963c7b550a5dcc1831d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-10-create-partitions"></a>Lezione 10: Creare partizioni
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione si creerà le partizioni per dividere la tabella FactInternetSales in parti logiche più piccole che possono essere elaborate (aggiornate) indipendentemente dalle altre. Per impostazione predefinita, ogni tabella inclusa nel modello dispone di una partizione, che comprende tutte le colonne e le righe della tabella. Per la tabella FactInternetSales, di voler dividere i dati per anno. una partizione per ognuno dei cinque anni della tabella. Ogni partizione può quindi essere elaborata in modo indipendente. Per altre informazioni, vedere [Tabella](../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 9: creare gerarchie](../analysis-services/lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Creare partizioni  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>Per creare partizioni nella tabella FactInternetSales  
  
1.  In Esplora modelli tabulari, espandere **tabelle**, fare doppio clic su **FactInternetSales** > **partizioni**.  
  
2.  Nella finestra di dialogo Gestione partizioni, fare clic su **copia**.  
  
3.  In **nome partizione**, modificare il nome in **FactInternetSales2010**.  
  
    > [!TIP]  
    > Nota: i nomi delle colonne nella finestra Anteprima tabella visualizzate le colonne incluse nella tabella del modello (selezionata) con i nomi di colonna dall'origine. Questo si verifica in quanto nella finestra Anteprima tabella vengono visualizzate le colonne della tabella di origine, non quelle della tabella del modello.  
  
4.  Selezionare il **SQL** pulsante sopra il lato destro della finestra di anteprima per aprire l'editor di istruzione SQL.  
  
    Poiché si desidera che la partizione includa solo le righe comprese in un determinato periodo, è necessario includere una clausola WHERE. È possibile creare una clausola WHERE solo tramite un'istruzione SQL.  
  
5.  Nel **istruzione SQL** campo, sostituire l'istruzione esistente copiando e incollando l'istruzione seguente:  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2010-01-01 00:00:00') AND ([OrderDate] < N'2011-01-01 00:00:00'))  
    ```  
  
    Questa istruzione specifica che la partizione deve includere tutti i dati delle righe in cui OrderDate si riferisce all'anno di calendario 2010, come specificato nella clausola WHERE.  
  
6.  Fare clic su **Convalida**.  
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>Per creare una partizione per l'anno 2011  
  
1.  Nell'elenco delle partizioni, fare clic su di **FactInternetSales2010** partizione appena creato e quindi fare clic su **copia**.  
  
2.  In **nome partizione**, tipo **FactInternetSales2011**.  
  
3.  Nell'istruzione SQL, affinché nella partizione siano incluse solo le righe per l'anno 2011, sostituire la clausola WHERE con la seguente:  
  
    ```  
    WHERE (([OrderDate] >= N'2011-01-01 00:00:00') AND ([OrderDate] < N'2012-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2012-year"></a>Per creare una partizione per l'anno 2012  
  
- Seguire i passaggi precedenti, utilizzando la seguente clausola WHERE. 
  
    ```  
    WHERE (([OrderDate] >= N'2012-01-01 00:00:00') AND ([OrderDate] < N'2013-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2013-year"></a>Per creare una partizione per l'anno 2013  
  
- Seguire i passaggi precedenti, utilizzando la seguente clausola WHERE. 
  
    ```  
    WHERE (([OrderDate] >= N'2013-01-01 00:00:00') AND ([OrderDate] < N'2014-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2014-year"></a>Per creare una partizione per l'anno 2014  
  
- Seguire i passaggi precedenti, utilizzando la seguente clausola WHERE. 
  
    ```  
    WHERE (([OrderDate] >= N'2014-01-01 00:00:00') AND ([OrderDate] < N'2015-01-01 00:00:00'))  
    ```  

## <a name="delete-the-factinternetsales-partition"></a>Eliminare la partizione FactInternetSales
Dopo aver creato le partizioni per ogni anno, è possibile eliminare la partizione di FactInternetSales. In questo modo si sovrappongono quando si sceglie elabora tutte quando si elaborano partizioni.
#### <a name="to-delete-the-factinternetsales-partition"></a>Per eliminare la partizione FactInternetSales
-  Fare clic sulla partizione FactInternetSales e quindi fare clic su **eliminare**.



## <a name="process-partitions"></a>Elaborare le partizioni  
In Gestione partizioni, si noti il **elaborati ultimo** colonna per ogni nuova partizione appena creato mostra queste partizioni non sono mai state elaborate. Quando si creano nuove partizioni, è necessario eseguire un'operazione di elaborazione delle partizioni o della tabella per aggiornare i dati nelle partizioni.  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>Per elaborare le partizioni FactInternetSales  
  
1.  Fare clic su **OK** per chiudere la finestra di dialogo Gestione partizioni.  
  
2.  Fare clic sul **FactInternetSales** tabella, quindi scegliere il **modello** menu > **processo** > **elabora partizioni**.  
  
3.  Nella finestra di dialogo Elabora partizioni verificare **modalità** è impostato su **elaborazione predefinita**.  
  
4.  Selezionare la casella di controllo **Elabora** per ognuna delle cinque partizioni create, quindi fare clic su **OK**.  

    ![come-tabulare-lesson10-processo-partizioni](../analysis-services/media/as-tabular-lesson10-process-partitions.png)
  
    Se viene chiesto di immettere le credenziali di rappresentazione, immettere il nome utente di Windows e la password specificati nella lezione 2.  
  
    Viene visualizzata la finestra di dialogo **Processo dati** , con informazioni dettagliate sul processo per ogni partizione. Si noti che per ogni partizione viene trasferito un numero diverso di righe. Questo avviene in quanto ogni partizione include solo le righe per l'anno specificato nella clausola WHERE dell'istruzione SQL. Al termine dell'elaborazione, proseguire e chiudere la finestra di dialogo Processo dati.  
  
    ![come tabulare-lesson10-processo-completamento](../analysis-services/media/as-tabular-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>Operazioni successive
Passare alla lezione successiva: [lezione 11: creare ruoli](../analysis-services/lesson-11-create-roles.md). 

