---
title: Mappa ad albero e grafici radiali in Reporting Services | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 08/31/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12307c8f-bca7-4d21-8ad5-0c07d819865b
caps.latest.revision: 17
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: e09afe4634c02db6e74413e7c1c10565450b3559
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="tree-map-and-sunburst-charts-in-reporting-services"></a>Mappa ad albero e grafici radiali in Reporting Services
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]

  La mappa ad albero e le visualizzazioni radiali di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sono ideali per la rappresentazione visiva dei dati gerarchici.   Questo argomento offre una panoramica su come aggiungere una mappa ad albero e un grafico radiale a un report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . L'argomento include anche una query Adventureworks di esempio come supporto nella fase iniziale.  
  
##  <a name="bkmk_treemap_chart"></a> Grafico della mappa ad albero  
 ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon")  
  
 Un grafico della mappa ad albero divide l'area del grafico in rettangoli che rappresentano i diversi livelli e le relative dimensioni della gerarchia dei dati. La mappa è simile ai rami degli alberi che iniziano dal tronco e si suddividono via via in rami sempre più piccoli. Ogni rettangolo viene suddiviso in rettangoli più piccoli che rappresentano il livello successivo nella gerarchia. I rettangoli della mappa ad albero al livello superiore presentano il rettangolo più grande nell'angolo superiore sinistro del grafico e il rettangolo più piccolo nell'angolo inferiore destro.  All'interno di ogni rettangolo, il livello successivo del rettangolo superiore presenta rettangoli dalla parte superiore sinistra fino in basso a destra.  
  
 Ad esempio, nell'immagine seguente della mappa ad albero di esempio, il territorio Sud-Ovest rappresenta il rettangolo più grande, mentre la Germania quello più piccolo. All'interno di del quadrato Sud-Ovest, il rettangolo Road Bikes è più grande del rettangolo Mountain Bikes.  
  
 ![ssrs_treemap_example](../../reporting-services/report-design/media/ssrs-treemap-example.png "ssrs_treemap_example")  
  
### <a name="to-insert-a-tree-map-chart-and-configure-for-the-sample-adventureworks-data"></a>Per inserire un grafico della mappa ad albero e configurare i dati Adventureworks di esempio  
 **Nota:** prima di aggiungere un grafico al report, creare un'origine dati e un set di dati.  Per i dati e una query di esempio, vedere la sezione [Dati Adventureworks di esempio](#bkmk_sample_data) in questo argomento.  
  
1.  Fare clic con il pulsante destro del mouse nell'area di progettazione, scegliere **Inserisci**, quindi selezionare **Grafico** .  
  
     Selezionare una mappa ad albero ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon").  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  Riposizionare e ridimensionare il grafico.   Per l'uso con i dati di esempio, è opportuno iniziare con un grafico di 5 pollici.  
  
3.  Aggiungere i seguenti campi dai dati di esempio:  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**Valori:** LineTotal<br /><br /> **Gruppi di categorie:** aggiungerle nell'ordine seguente:<br /><br /> 1) CategoryName<br /><br /> 2) SubcategoryName<br /><br /> **Gruppi di serie:** TerritoryName|  
  
4.  Per ottimizzare le dimensioni della pagina per la forma generale di una mappa ad albero, impostare la posizione della legenda nella parte inferiore.  
  
5.  Per aggiungere descrizioni di comando che consentono di visualizzare la sottocategoria e il totale della riga, fare clic con il pulsante destro del mouse su **LineTotal** , quindi selezionare **Proprietà serie**.  
  
     ![ssrs_visualization_seriesproperties](../../reporting-services/report-design/media/ssrs-visualization-seriesproperties.png "ssrs_visualization_seriesproperties")  
  
     Impostare la proprietà **Descrizione comando** come riportato di seguito:  
  
    ```  
    =Fields!SubcategoryName.Value &": " &Format(Sum(Fields!LineTotal.Value),"C")  
    ```  
  
     Per altre informazioni, vedere [Visualizzazione di descrizioni comandi in una serie &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md).  
  
6.  Modificare il titolo predefinito del grafico su "Categorized Sales by Territory".  
  
7.  Il numero di valori di etichetta visualizzati dipende dalle dimensioni del carattere, dalle dimensioni dell'area totale del grafico e dalle dimensioni dei rettangoli specifici.  Per visualizzare più etichette, impostare la proprietà del carattere Etichetta di LineTotal su 10 pt invece del valore predefinito di 8 pt.  
  
  
##  <a name="bkmk_sunburst_chart"></a> Grafico radiale  
 ![ssrs_sunburst_icon](../../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon")  
  
 In un grafico radiale la gerarchia è rappresentata da una serie di cerchi, con il livello superiore della gerarchia al centro e i livelli inferiori come anelli concentrici.  Il livello più basso della gerarchia è rappresentato dall'anello esterno.  
  
 ![ssrs_sunburst_example](../../reporting-services/report-design/media/ssrs-sunburst-example.png "ssrs_sunburst_example")  
  
### <a name="to-insert-a-sunburst-chart-and-configure-for-the-sample-adventureworks-data"></a>Per inserire un grafico radiale e configurare i dati Adventureworks di esempio  
 **Nota:** prima di aggiungere un grafico al report, creare un'origine dati e un set di dati.  Per i dati e una query di esempio, vedere la sezione [Dati Adventureworks di esempio](#bkmk_sample_data) in questo argomento.  
  
1.  Fare clic con il pulsante destro del mouse nell'area di progettazione, scegliere **Inserisci**, quindi selezionare **Grafico** .  
  
     Selezionare il grafico radiale ![ssrs_treemap_icon](../../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon").  
  
     ![ssrs_insert_treemap_sunburst](../../reporting-services/report-design/media/ssrs-insert-treemap-sunburst.png "ssrs_insert_treemap_sunburst")  
  
2.  Riposizionare e ridimensionare il grafico.   Per l'uso con i dati di esempio, è opportuno iniziare con un grafico di 5 pollici.  
  
3.  Aggiungere i seguenti campi dai dati di esempio:  
  
    |||  
    |-|-|  
    |![ssrs_treemap_example_properties](../../reporting-services/report-design/media/ssrs-treemap-example-properties.png "ssrs_treemap_example_properties")|**Valori:** LineTotal<br /><br /> **Gruppi di categorie:** aggiungerle nell'ordine seguente:<br /><br /> 1) CategoryName<br /><br /> 2) SubcategoryName<br /><br /> 3) SalesReasonName<br /><br /> **Gruppi di serie:** TerritoryName.|  
  
4.  Per ottimizzare le dimensioni della pagina per la forma generale di un grafico radiale, impostare la posizione della legenda nella parte inferiore.  
  
5.  Modificare il titolo predefinito del grafico su "Categorized Sales by Territory, with sales reason".  
  
6.  |||  
    |-|-|  
    |![ssrs_sunburst_linetotalproperties](../../reporting-services/report-design/media/ssrs-sunburst-linetotalproperties.png "ssrs_sunburst_linetotalproperties")|Per aggiungere i valori dei gruppi di categoria al grafico radiale come etichette, impostare la proprietà dell'etichetta come segue: **Visible** = true e **UseValueAsLabel**=False.<br /><br /> I valori di etichetta visualizzati dipendono dalle dimensioni del carattere, dalle dimensioni dell'area totale del grafico e dalle dimensioni dei rettangoli specifici.  Per visualizzare più etichette, impostare la proprietà del carattere Etichetta di LineTotal su 8 pt invece del valore predefinito di 10 pt.|  
  
7.  Se si desidera una combinazione di colori diversa, modificare la proprietà **Tavolozza** del grafico.  
  
     ![ssrs_visualization_palette](../../reporting-services/report-design/media/ssrs-visualization-palette.png "ssrs_visualization_palette")  
  
  
##  <a name="bkmk_sample_data"></a> Dati Adventureworks di esempio  
 Questa sezione include una query di esempio e la procedura di base per la creazione di un'origine e di un set di dati in [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]. Se il report contiene già un'origine e un set di dati, ignorare questa sezione.  
  
 La query restituisce dati dettagliati sugli ordini di vendita Adventureworks con il territorio di vendita, la categoria e la sottocategoria del prodotto e la data del motivo della vendita.  
  
1.  **Ottenere i dati:**  
  
     La query in questa sezione è basata sul database Adventureworks, disponibile per il download da  [Adventure Works 2014 Full Database Backup (Backup completo del database Adventure Works 2014)](https://msftdbprodsamples.codeplex.com/releases/view/125550).  
  
     Per altre informazioni su come installare il database, vedere [How to install Adventure Works 2014 Sample Databases.pdf](https://msftdbprodsamples.codeplex.com/releases/view/125550).  
  
2.  **Creare un'origine dati:**  
  
    1.  Nel riquadro **Dati report** fare clic con il pulsante destro del mouse su **Origini dati** e selezionare **Aggiungi origine dati**.  
  
    2.  Selezionare **Usa una connessione incorporata nel report**.  
  
    3.  Selezionare il tipo di connessione **Microsoft SQL Server**.  
  
    4.  Digitare la stringa di connessione per il server e il database, ad esempio la seguente:  
  
        ```  
        Data Source=[server name];Initial Catalog=AdventureWorks2014  
        ```  
  
    5.  Eseguire una verifica con il pulsante **Test connessione** e quindi fare clic su **OK**.  
  
     Per altre informazioni sulla creazione di un'origine dati, vedere [Aggiungere e verificare una connessione dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md).  
  
3.  **Creare un set di dati:**  
  
    -   Nel riquadro **Dati report** fare clic con il pulsante destro del mouse su **Set di dati** e quindi scegliere **Aggiungi set di dati**.  
  
    -   Scegliere **Utilizzare un set di dati incorporato nel report**.  
  
    -   Selezionare l'origine dati creata nei passaggi precedenti.  
  
    -   Selezionare il tipo di query **Testo** e quindi copiare e incollare la query seguente nella casella di testo **Query** :  
  
        ```  
        SELECT    Sales.SalesOrderHeader.SalesOrderID, Sales.SalesOrderHeader.OrderDate, Sales.SalesOrderDetail.SalesOrderDetailID, Sales.SalesOrderDetail.ProductID, Sales.SalesOrderDetail.LineTotal,   
                                 Sales.SalesOrderDetail.UnitPrice, Sales.SalesOrderDetail.OrderQty, Production.Product.Name, Production.Product.ProductNumber, Sales.SalesTerritory.TerritoryID, lower(Sales.SalesTerritory.Name) AS TerritoryName,   
                                 Production.ProductSubcategory.Name AS SubcategoryName, Production.ProductCategory.Name AS CategoryName, Sales.SalesReason.SalesReasonID, Sales.SalesReason.Name AS SalesReasonName  
        FROM            Sales.SalesOrderDetail INNER JOIN  
                                 Sales.SalesOrderHeader ON Sales.SalesOrderDetail.SalesOrderID = Sales.SalesOrderHeader.SalesOrderID INNER JOIN  
                                 Production.Product ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID INNER JOIN  
                                 Sales.SalesTerritory ON Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID AND   
                                 Sales.SalesOrderHeader.TerritoryID = Sales.SalesTerritory.TerritoryID INNER JOIN  
                                 Production.ProductSubcategory ON Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID AND   
                                 Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID INNER JOIN  
                                 Production.ProductCategory ON Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID AND   
                                 Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID INNER JOIN  
                                 Sales.SalesOrderHeaderSalesReason ON Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID AND   
                                 Sales.SalesOrderHeader.SalesOrderID = Sales.SalesOrderHeaderSalesReason.SalesOrderID INNER JOIN  
                                 Sales.SalesReason ON Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID AND   
                                 Sales.SalesOrderHeaderSalesReason.SalesReasonID = Sales.SalesReason.SalesReasonID  
        ```  
  
    -   scegliere **OK**.  
  
     Per altre informazioni sulla creazione di un set di dati, vedere [Creare un set di dati condiviso o un set di dati incorporato &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md).  
  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzazione di progettazione set di dati condivisi &#40;Generatore report&#41;](../../reporting-services/report-builder/shared-dataset-design-view-report-builder.md)   
 [Visualizzazione di descrizioni comandi in una serie &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/show-tooltips-on-a-series-report-builder-and-ssrs.md)   
 [Esercitazione: Mappe ad albero in Power BI](https://support.powerbi.com/knowledgebase/articles/556200-tutorial-treemaps-in-power-bi)   
 [Treemap: Microsoft Research Data Visualization Apps for Office (Mappa ad albero: App di visualizzazione dati di Microsoft Research per Office)](http://research.microsoft.com/en-us/projects/msrdatavis/treemap.aspx)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../../includes/feedback-stackoverflow-msdn-connect-md.md)]


