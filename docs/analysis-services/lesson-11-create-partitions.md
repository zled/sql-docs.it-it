---
title: "Lezione 11: Creare partizioni | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
caps.latest.revision: 28
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Lezione 11: Creare partizioni
In questa lezione verranno create partizioni per dividere la tabella Internet Sales in parti logiche più piccole, che possono essere elaborate (aggiornate) indipendentemente dalle altre partizioni. Per impostazione predefinita, ogni tabella inclusa nel modello dispone di una partizione, che comprende tutte le colonne e le righe della tabella. Per la tabella Internet Sales, si desidera dividere i dati in base all'anno, creando una partizione per ognuno dei cinque anni della tabella.  Ogni partizione può quindi essere elaborata in modo indipendente. Per altre informazioni, vedere [Partizioni &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione è necessario aver completato la lezione precedente: [Lezione 10: Creare gerarchie](../analysis-services/lesson-10-create-hierarchies.md).  
  
## Creare partizioni  
  
#### Per creare partizioni nella tabella Internet Sales  
  
1.  In Progettazione modelli fare clic sulla tabella **Internet Sales**, quindi scegliere **Partizioni** dal menu **Tabella**.  
  
    Verrà visualizzata la finestra di dialogo **Gestione partizioni**.  
  
2.  Nell'elenco delle partizioni della finestra di dialogo **Gestione partizioni** fare clic sulla partizione **Internet Sales**.  
  
3.  In **Nome partizione** modificare il nome in **Internet Sales 2010**.  
  
    > [!TIP]  
    > Prima di continuare con il passaggio successivo, osservare che per i nomi di colonna nella finestra Anteprima tabella vengono visualizzate le colonne incluse nella tabella del modello (selezionate) con i nomi di colonna dell'origine. Questo si verifica in quanto nella finestra Anteprima tabella vengono visualizzate le colonne della tabella di origine, non quelle della tabella del modello.  
  
4.  Fare clic sul pulsante **Editor di query** nella parte superiore destra della finestra di anteprima.  
  
    Poiché si desidera che la partizione includa solo le righe comprese in un determinato periodo, è necessario includere una clausola WHERE. È possibile creare una clausola WHERE solo tramite un'istruzione SQL.  
  
5.  Nel campo **Istruzione SQL** sostituire l'istruzione esistente incollando l'istruzione seguente:  
  
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
  
  
#### Per creare una partizione per l'anno 2011  
  
1.  Nell'elenco delle partizioni fare clic sulla partizione **Internet Sales 2010** appena creata e scegliere **Copia**.  
  
2.  In **Nome partizione** digitare **Internet Sales 2011**.  
  
3.  Nell'istruzione SQL, affinché nella partizione siano incluse solo le righe per l'anno 2011, sostituire la clausola WHERE con la seguente:  
  
    ```  
    WHERE (([OrderDate] >= N'2011-01-01 00:00:00') AND ([OrderDate] < N'2012-01-01 00:00:00'))  
    ```  
  
#### Per creare una partizione per l'anno 2012  
  
1.  Nella finestra di dialogo **Gestione partizioni** fare clic su **Copia**.  
  
2.  In **Nome partizione** digitare **Internet Sales 2012**.  
  
3.  Nell'istruzione SQL, affinché nella partizione siano incluse solo le righe per l'anno 2012, sostituire la clausola WHERE con la seguente:  
  
    ```  
    WHERE (([OrderDate] >= N'2012-01-01 00:00:00') AND ([OrderDate] < N'2013-01-01 00:00:00'))  
    ```  
  
#### Per creare una partizione per l'anno 2013  
  
1.  Nella finestra di dialogo **Gestione partizioni** fare clic su **Nuova**.  
  
2.  In **Nome partizione** digitare **Internet Sales 2013**.  
  
3.  Nell'istruzione SQL, affinché nella partizione siano incluse solo le righe per l'anno 2013, sostituire la clausola WHERE con la seguente:  
  
    ```  
    WHERE (([OrderDate] >= N'2013-01-01 00:00:00') AND ([OrderDate] < N'2014-01-01 00:00:00'))  
    ```  
  
#### Per creare una partizione per l'anno 2014 nella tabella Internet Sales  
  
1.  Nella finestra di dialogo **Gestione partizioni** fare clic su **Nuova**.  
  
2.  In **Nome partizione** digitare **Internet Sales 2014**.  
  
3.  Nell'istruzione SQL, affinché nella partizione siano incluse solo le righe per l'anno 2014, sostituire la clausola WHERE con la seguente:  
  
    ```  
    WHERE (([OrderDate] >= N'2014-01-01 00:00:00') AND ([OrderDate] < N'2015-01-01 00:00:00'))  
    ```  
  
## Elaborare le partizioni  
Nella finestra di dialogo **Gestione partizioni**, notare l'asterisco (**\***) accanto ai nomi di partizione per ognuna delle nuove partizioni appena create. L'asterisco indica che la partizione non è stata elaborata (aggiornata). Quando si creano nuove partizioni, è necessario eseguire un'operazione di elaborazione delle partizioni o della tabella per aggiornare i dati nelle partizioni.  
  
#### Per elaborare le partizioni di Internet Sales  
  
1.  Fare clic su **OK** per chiudere la finestra di dialogo **Gestione partizioni**.  
  
2.  In Progettazione modelli fare clic sulla tabella **Internet Sales**, scegliere **Elabora** (Aggiorna) nel menu **Modello**, quindi fare clic su **Elabora partizioni**.  
  
3.  Nella finestra di dialogo **Elabora partizioni** verificare che l'opzione **Modalità** sia impostata su **Elaborazione predefinita**.  
  
4.  Selezionare la casella di controllo **Elabora** per ognuna delle cinque partizioni create, quindi fare clic su **OK**.  
  
    Se vengono richieste le credenziali di rappresentazione, immettere il nome utente e la password di Windows specificati al passaggio 6 della lezione 2.  
  
    Viene visualizzata la finestra di dialogo **Processo dati**, con informazioni dettagliate sul processo per ogni partizione. Si noti che per ogni partizione viene trasferito un numero diverso di righe. Questo avviene in quanto ogni partizione include solo le righe per l'anno specificato nella clausola WHERE dell'istruzione SQL. Al termine dell'elaborazione, proseguire e chiudere la finestra di dialogo Processo dati.  
  
  
  
## Passaggi successivi  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 12: Creare ruoli](../analysis-services/lesson-12-create-roles.md).  
  
  
  
