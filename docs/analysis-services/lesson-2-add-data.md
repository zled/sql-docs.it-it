---
title: "Lezione 2: Aggiungere dati | Microsoft Docs"
ms.custom: ""
ms.date: "03/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 13c3a8cc-b1db-4aba-ad9b-038b7971be8d
caps.latest.revision: 33
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 24
---
# Lezione 2: Aggiungere dati
In questa lezione verrà utilizzata l'Importazione guidata tabella in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] per connettersi al database SQL AdventureWorksDW, selezionare i dati, visualizzare un'anteprima, filtrare i dati e quindi importarli nell'area di lavoro del modello.  
  
Utilizzando l'Importazione guidata tabella è possibile importare dati da diverse origini relazionali, quali Access, SQL, Oracle, Sybase, Informix, DB2, Teradata e così via. I passaggi per l'importazione dei dati da ognuna di queste origini relazionali sono molto simili a quanto descritto di seguito. I dati possono inoltre essere selezionati utilizzando una stored procedure.  
  
Per altre informazioni sull'importazione di dati e sui diversi tipi di origine dati da cui è possibile importare, vedere [Origini dati &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/data-sources-ssas-tabular.md).  
  
Tempo stimato per il completamento della lezione: **20 minuti**  
  
## Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario aver completato la lezione precedente: [Lezione 1: Creare un nuovo modello di progetto tabulare](../analysis-services/lesson-1-create-a-new-tabular-model-project.md).  
  
## Creare una connessione  
  
#### Per creare una connessione al database AdventureWorksDW2012  
  
1.  In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] fare clic sul menu **Modello** e scegliere **Importa da origine dati**.  
  
    Verrà avviata l'Importazione guidata tabella, che consente di eseguire i passaggi per l'impostazione di una connessione a un'origine dati. Se la voce **Importa da origine dati** è disattivata, fare doppio clic su **Model.bim** in **Esplora soluzioni** per aprire il modello nella finestra di progettazione.  
  
2.  Nell'**Importazione guidata tabella**, in **Database relazionali** fare clic su **Microsoft SQL Server** e su **Avanti**.  
  
3.  Nella pagina **Connessione a un database di Microsoft SQL Server**, in **Nome descrittivo connessione** digitare **Adventure Works DB da SQL**.  
  
4.  In **Nome server** digitare il nome del server in cui è installato il database AdventureWorksDW.  
  
5.  Nel campo **Nome database** fare clic sulla freccia giù, selezionare **AdventureWorksDW** e scegliere **Avanti**.  
  
6.  Nella pagina **Impostazioni di rappresentazione** specificare le credenziali usate da Analysis Services per la connessione all'origine dati quando vengono importati ed elaborati i dati. Verificare che l'opzione **Nome utente e password specifici di Windows** sia selezionata, immettere le credenziali di accesso a Windows in **Nome utente** e **Password** e fare clic su **Avanti**.  
  
    > [!NOTE]  
    > L'utilizzo di un account utente e una password di Windows rappresenta il metodo più sicuro per la connessione a un'origine dati. Per altre informazioni, vedere [Rappresentazione &#40;SSAS tabulare&#41;](../analysis-services/tabular-models/impersonation-ssas-tabular.md).  
  
7.  Nella pagina **Scelta della modalità di importazione dei dati** verificare che l'opzione **Seleziona da un elenco di tabelle e viste per scegliere i dati da importare** sia selezionata. Poiché si vuole selezionare da un elenco di tabelle e viste, fare clic su **Avanti** per visualizzare un elenco di tutte le tabelle di origine nel database di origine.  
  
8.  Nella pagina **Selezione tabelle e viste** selezionare le caselle di controllo corrispondenti alle tabelle seguenti: **DimCustomer**, **DimDate**, **DimGeography**, **DimProduct**, **DimProductCategory**, **DimProductSubcategory** e **FactInternetSales**.  
  
9. Si desidera fornire nomi più comprensibili per le tabelle nel modello. Fare clic sulla cella nella colonna **Nome descrittivo** per **DimCustomer**. Rinominare la tabella rimuovendo "Dim" da DimCustomer.  
  
10. Rinominare le altre tabelle:  
  
    |Nome origine|Nome descrittivo|  
    |---------------|-----------------|  
    |DimDate|Data|  
    |DimGeography|Geography|  
    |DimProduct|Product|  
    |DimProductCategory|Product Category|  
    |DimProductSubcategory|Product Subcategory|  
    |FactInternetSales|Internet Sales|  
  
    **NON** fare clic su **Fine**.  
  
Dopo avere stabilito la connessione al database, avere selezionato le tabelle da importare e avere assegnato nomi descrittivi alle tabelle, passare alla sezione successiva per [filtrare i dati della tabella prima dell'importazione](#FilterData).  
  
## <a name="FilterData"></a>Filtrare i dati della tabella  
La tabella DimCustomer importata dal database contiene un subset dei dati del database SQL Server Adventure Works originale. Verrà utilizzato un filtro per escludere alcune colonne della tabella DimCustomer che non sono necessarie. Quando possibile, utilizzare filtri per escludere dati che non verranno utilizzati, per risparmiare spazio in memoria utilizzato dal modello.  
  
#### Per filtrare i dati della tabella prima dell'importazione  
  
1.  Selezionare la riga per la tabella **Customer** e fare clic su **Visualizza anteprima e applica filtro**. Verrà visualizzata la finestra **Anteprima tabella selezionata** in cui sono visualizzate tutte le colonne della tabella di origine DimCustomer visualizzata.  
  
2.  Deselezionare la casella di controllo nella parte superiore delle colonne seguenti.  
  
    |Customer|  
    |------------|  
    |**SpanishEducation**|  
    |**FrenchEducation**|  
    |**SpanishOccupation**|  
    |**FrenchOccupation**|  
  
    Poiché i valori per queste colonne non sono attinenti all'analisi delle vendite Internet, non è necessario importare queste colonne. Eliminando le colonne non necessarie, è possibile ridurre le dimensioni del modello.  
  
3.  Verificare che tutte le altre colonne siano selezionate e fare clic su **OK**.  
  
    Si noti che viene visualizzata la dicitura **Filtri applicati** nella colonna **Dettagli filtro** nella riga **Customer**. Se si fa clic su tale collegamento, viene visualizzata una descrizione testuale dei filtri appena applicati.  
  
4.  Filtrare le tabelle restanti deselezionando le caselle di controllo per le colonne seguenti in ogni tabella:  
  
    |Data|  
    |--------|  
    |**DateKey**|  
    |**SpanishDayNameOfWeek**|  
    |**FrenchDayNameOfWeek**|  
    |**SpanishMonthName**|  
    |**FrenchMonthName**|  
  
    |Geography|  
    |-------------|  
    |**SpanishCountryRegionName**|  
    |**FrenchCountryRegionName**|  
    |**IpAddressLocator**|  
  
    |Product|  
    |-----------|  
    |**SpanishProductName**|  
    |**FrenchProductName**|  
    |**FrenchDescription**|  
    |**ChineseDescription**|  
    |**ArabicDescription**|  
    |**HebrewDescription**|  
    |**ThaiDescription**|  
    |**GermanDescription**|  
    |**JapaneseDescription**|  
    |**TurkishDescription**|  
  
    |Categoria prodotto|  
    |--------------------|  
    |**SpanishProductCategoryName**|  
    |**FrenchProductCategoryName**|  
  
    |Product Subcategory|  
    |-----------------------|  
    |**SpanishProductSubcategoryName**|  
    |**FrenchProductSubcategoryName**|  
  
    |Internet Sales|  
    |------------------|  
    |**OrderDateKey**|  
    |**DueDateKey**|  
    |**ShipDateKey**|  
  
Dopo avere visualizzato l'anteprima ed escluso tramite filtro i dati non necessari, è possibile importare i dati. Passare alla sezione successiva **Importare i dati di tabelle e colonna selezionati**.  
  
## <a name="Import"></a>Importare i dati di tabella e colonna selezionati  
È ora possibile importare i dati selezionati. La procedura guidata consente di importare i dati delle tabelle e qualsiasi relazione presente tra le tabelle. Nel modello verranno create nuove tabelle e colonne utilizzando i nomi descrittivi specificati e i dati esclusi tramite filtro non verranno importati.  
  
#### Per importare i dati delle tabelle e delle colonne selezionati  
  
1.  Verificare le selezioni. Se sono corrette, fare clic su **Fine**.  
  
    Durante l'importazione dei dati la procedura guidata visualizza il numero di righe recuperate. Una volta importati tutti i dati, verrà visualizzato un messaggio in cui viene indicato il completamento dell'operazione.  
  
    > [!TIP]  
    > Per vedere le relazioni create automaticamente tra le tabelle importate, fare clic su **Dettagli** nella riga **Preparazione dati**.  
  
2.  Scegliere **Chiudi**.  
  
    La procedura guidata verrà chiusa e verrà visualizzata la finestra Progettazione modelli. Ogni tabella è stata aggiunta come nuova scheda in Progettazione modelli.  
  
## Salvare il progetto di modello.  
È importante salvare frequentemente il progetto di modello.  
  
#### Per salvare il progetto di modello  
  
-   In [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] scegliere **Salva tutto** dal menu **File**.  
  
## Passaggio successivo  
Per continuare questa esercitazione, passare alla lezione successiva: [Lezione 3: Rinominare colonne](../analysis-services/lesson-3-rename-columns.md).  
  
  
  
