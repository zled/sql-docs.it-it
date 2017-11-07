---
title: Programmazione di oggetti di base OLAP in AMO | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- programming [AMO]
- Analysis Management Objects, OLAP
- OLAP [AMO]
- AMO, OLAP
ms.assetid: ad1c970e-c0cb-4687-9563-56ab62c2db5f
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: eaca145753958228bdecae9b7bdcb2ebcdb8b6cb
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="programming-amo-olap-basic-objects"></a>Programmazione di oggetti di base OLAP in AMO
  La creazione di oggetti di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] complessi è un'operazione estremamente semplice per cui è necessario tuttavia prestare attenzione ai dettagli. In questo argomento vengono descritti i dettagli relativi alla programmazione di oggetti di base OLAP. In questo argomento sono incluse le sezioni seguenti:  
  
-   [Oggetti Dimension](#Dim)  
  
-   [Oggetti del cubo](#Cub)  
  
-   [Oggetti MeasureGroup](#MG)  
  
-   [Oggetti Partition](#Part)  
  
-   [Oggetti Aggregation](#AD)  
  
##  <a name="Dim"></a>Oggetti Dimension  
 Per amministrare o elaborare una dimensione, programmare l'oggetto <xref:Microsoft.AnalysisServices.Dimension>.  
  
### <a name="creating-dropping-and-finding-a-dimension"></a>Creazione, eliminazione e individuazione di una dimensione  
 La creazione di un oggetto <xref:Microsoft.AnalysisServices.Dimension> viene realizzata in quattro passaggi:  
  
1.  Creazione dell'oggetto dimensione e popolamento degli attributi di base.  
  
     Gli attributi di base sono Nome, Tipo dimensione, Modalità di archiviazione, Associazione origine dati, Nome membro Totale attributo e altri attributi della dimensione.  
  
     Prima di creare una dimensione, è necessario verificare che non esista già. Se la dimensione esiste, viene eliminata e quindi ricreata.  
  
2.  Creazione degli attributi che definiscono la dimensione.  
  
     Prima di utilizzare un attributo, è necessario aggiungerlo singolarmente allo schema (individuare il metodo CreateDataItem alla fine del codice di esempio). Successivamente è possibile aggiungere tale attributo alla raccolta di attributi della dimensione.  
  
     La colonna chiave e quella relativa la nome devono essere definite in tutti gli attributi.  
  
     L'attributo chiave primaria della dimensione deve essere definito come AttributeUsage.Key per indicare in modo chiaro che tale attributo rappresenta l'accesso principale alla dimensione.  
  
3.  Creazione delle gerarchie cui l'utente avrà accesso per navigare nella dimensione.  
  
     Durante la creazione delle gerarchie, l'ordine del livello viene definito dall'ordine in cui i livelli vengono creati, dall'alto verso il basso. Il livello più alto è il primo aggiunto alla raccolta di livelli della gerarchia.  
  
4.  Aggiornamento del server tramite il metodo Update della dimensione corrente.  
  
 Esempio di codice seguente crea la dimensione prodotto dalla tabella products Adventure Works nel database di esempio.  
  
```  
static void CreateProductDimension(Database db, string datasourceName)  
{  
    // Create the Product dimension  
    Dimension dim = db.Dimensions.FindByName("Product");  
    if ( dim != null)  
       dim.Drop();  
    dim = db.Dimensions.Add("Product");  
    dim.Type = DimensionType.Products;  
    dim.UnknownMember = UnknownMemberBehavior.Hidden;  
    dim.AttributeAllMemberName = "All Products";  
    dim.Source = new DataSourceViewBinding(datasourceName);  
    dim.StorageMode = DimensionStorageMode.Molap;  
  
    #region Create attributes  
  
    DimensionAttribute attr;  
  
    attr = dim.Attributes.Add("Product Name");  
    attr.Usage = AttributeUsage.Key;  
    attr.Type = AttributeType.Product;  
    attr.OrderBy = OrderBy.Name;  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ProductKey"));  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProduct", "EnglishProductName");  
  
    attr = dim.Attributes.Add("Product Line");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ProductLine"));  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProduct", "ProductLineName");  
  
    attr = dim.Attributes.Add("Model Name");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ModelName"));  
    attr.AttributeRelationships.Add(new AttributeRelationship("Product Line"));  
    attr.AttributeRelationships.Add(new AttributeRelationship("Subcategory"));  
  
    attr = dim.Attributes.Add("Subcategory");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProductSubcategory", "ProductSubcategoryKey"));  
    attr.KeyColumns[0].NullProcessing = NullProcessing.UnknownMember;  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProductSubcategory", "EnglishProductSubcategoryName");  
    attr.AttributeRelationships.Add(new AttributeRelationship("Category"));  
  
    attr = dim.Attributes.Add("Category");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProductCategory", "ProductCategoryKey"));  
    attr.NameColumn = CreateDataItem(db.DataSourceViews[0], "DimProductCategory", "EnglishProductCategoryName");  
  
    attr = dim.Attributes.Add("List Price");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "ListPrice"));  
    attr.AttributeHierarchyEnabled = false;  
  
    attr = dim.Attributes.Add("Size");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "Size"));  
    attr.AttributeHierarchyEnabled = false;  
  
    attr = dim.Attributes.Add("Weight");  
    attr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "DimProduct", "Weight"));  
    attr.AttributeHierarchyEnabled = false;  
  
    #endregion  
  
    #region Create hierarchies  
  
    Hierarchy hier;  
  
    hier = dim.Hierarchies.Add("Product Model Categories");  
    hier.AllMemberName = "All Products";  
    hier.Levels.Add("Category").SourceAttributeID = "Category";  
    hier.Levels.Add("Subcategory").SourceAttributeID = "Subcategory";  
    hier.Levels.Add("Model Name").SourceAttributeID = "Model Name";  
  
    hier = dim.Hierarchies.Add("Product Categories");  
    hier.AllMemberName = "All Products";  
    hier.Levels.Add("Category").SourceAttributeID = "Category";  
    hier.Levels.Add("Subcategory").SourceAttributeID = "Subcategory";  
    hier.Levels.Add("Model Name").SourceAttributeID = "Product Name";  
  
    hier = dim.Hierarchies.Add("Product Model Lines");  
    hier.AllMemberName = "All Products";  
    hier.Levels.Add("Subcategory").SourceAttributeID = "Product Line";  
    hier.Levels.Add("Model Name").SourceAttributeID = "Model Name";  
  
    #endregion  
  
    dim.Update();  
}  
  
static DataItem CreateDataItem(DataSourceView dsv, string tableName, string columnName)  
{  
    DataTable dataTable = ((DataSourceView)dsv).Schema.Tables[tableName];  
    DataColumn dataColumn = dataTable.Columns[columnName];  
    return new DataItem(tableName, columnName,  
        OleDbTypeConverter.GetRestrictedOleDbType(dataColumn.DataType));  
}  
  
```  
  
### <a name="processing-a-dimension"></a>Elaborazione di una dimensione  
 L'elaborazione di una dimensione è semplice come l'utilizzo del metodo Process dell'oggetto <xref:Microsoft.AnalysisServices.Dimension>.  
  
 L'elaborazione di una dimensione può influire su tutti i cubi che utilizzano la dimensione stessa. Per ulteriori informazioni sulle opzioni di elaborazione, vedere [l'elaborazione di un modello multidimensionale &#40; Analysis Services &#41; ](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Nel codice seguente viene eseguito un aggiornamento incrementale in tutte le dimensioni di un database specificato:  
  
```  
static void UpdateAllDimensions(Database db)  
{  
    foreach (Dimension dim in db.Dimensions)  
        dim.Process(ProcessType.ProcessUpdate);  
}  
```  
  
##  <a name="Cub"></a>Oggetti del cubo  
 Per amministrare o elaborare un cubo, programmare l'oggetto <xref:Microsoft.AnalysisServices.Cube>.  
  
### <a name="creating-dropping-and-finding-a-cube"></a>Creazione, eliminazione e individuazione di un cubo  
 La gestione dei cubi è analoga a quella delle dimensioni. La creazione di un oggetto <xref:Microsoft.AnalysisServices.Cube> viene realizzata in quattro passaggi:  
  
1.  Creazione dell'oggetto cubo e popolamento degli attributi di base.  
  
     Gli attributi di base sono Nome, Modalità di archiviazione, Associazione origine dati, Misura predefinita e altri attributi del cubo.  
  
     Prima di creare un cubo, è necessario verificare che non esista. Nell'esempio, se il cubo esiste viene eliminato e quindi ricreato.  
  
2.  Aggiunta delle dimensioni del cubo.  
  
     Le dimensioni vengono aggiunte alla raccolta corrente di dimensioni del cubo dal database. Le dimensioni del cubo costituiscono i riferimenti alla raccolta di dimensioni del database. Per ogni dimensione il mapping al cubo deve essere eseguito singolarmente. Per eseguire il mapping delle dimensioni, nell'esempio vengono forniti l'identificatore interno delle dimensioni del database, un nome per la dimensione del cubo e un ID per la dimensione denominata del cubo.  
  
     Nel codice di esempio si noti che la dimensione "Date" viene aggiunta tre volte, ogni volta utilizzando un nome di dimensione del cubo diverso, ovvero Date, Ship Date e Delivery Date. Tali dimensioni vengono denominate dimensioni "con ruoli multipli". La dimensione di base è la stessa (Date), ma nella tabella dei fatti la dimensione viene utilizzata in "ruoli" diversi (Order Date, Ship Date, Delivery Date). Per informazioni sulla definizione delle dimensioni "con ruoli multipli", vedere "Creazione, eliminazione e individuazione di un oggetto MeasureGroup" più avanti in questo argomento.  
  
3.  Creazione dei gruppi di misure cui l'utente avrà accesso per visualizzare i dati del cubo.  
  
     La creazione di un gruppo di misure verrà descritta in "Creazione, eliminazione e individuazione di un oggetto MeasureGroup" più avanti in questo argomento. Nell'esempio viene eseguito il wrapping della creazione dei gruppi di misure in metodi diversi, uno per ciascun gruppo.  
  
4.  Aggiornamento del server tramite il metodo Update del cubo corrente.  
  
     Il metodo Update viene utilizzato con il parametro UpdateOptions.ExpandFull per garantire l'aggiornamento completo di tutti gli oggetti nel server.  
  
 Nell'esempio di codice seguente vengono create le parti del cubo Adventure Works. Nell'esempio di codice non viene eseguita la creazione di tutte le dimensioni o di tutti i gruppi di misure inclusi nell'esempio Adventure Works Analysis Services Project.  
  
```  
static void CreateAdventureWorksCube(Database db, string datasourceName)  
{  
    // Create the Adventure Works cube  
    Cube cube = db.Cubes.FindByName("Adventure Works");  
    if ( cube != null)  
       cube.Drop();  
    db.Cubes.Add("Adventure Works");  
    cube.DefaultMeasure = "[Reseller Sales Amount]";  
    cube.Source = new DataSourceViewBinding(datasourceName);  
    cube.StorageMode = StorageMode.Molap;  
  
    #region Create cube dimensions  
  
    Dimension dim;  
  
    dim = db.Dimensions.GetByName("Date");  
    cube.Dimensions.Add(dim.ID, "Date", "Order Date Key - Dim Time");  
    cube.Dimensions.Add(dim.ID, "Ship Date",  
        "Ship Date Key - Dim Time");  
    cube.Dimensions.Add(dim.ID, "Delivery Date",  
        "Delivery Date Key - Dim Time");  
  
    dim = db.Dimensions.GetByName("Customer");  
    cube.Dimensions.Add(dim.ID);  
  
    dim = db.Dimensions.GetByName("Reseller");  
    cube.Dimensions.Add(dim.ID);  
    #endregion  
  
    #region Create measure groups  
  
    CreateSalesReasonsMeasureGroup(cube);  
    CreateInternetSalesMeasureGroup(cube);  
    CreateResellerSalesMeasureGroup(cube);  
    CreateCustomersMeasureGroup(cube);  
    CreateCurrencyRatesMeasureGroup(cube);  
  
    #endregion  
  
    cube.Update(UpdateOptions.ExpandFull);  
}  
```  
  
### <a name="processing-a-cube"></a>Elaborazione di un cubo  
 L'elaborazione di un cubo è semplice come l'utilizzo del metodo Process dell'oggetto <xref:Microsoft.AnalysisServices.Cube>. L'elaborazione di un cubo comporta l'elaborazione di tutti i gruppi di misure del cubo e di tutte le partizioni del gruppo di misure. In un cubo le partizioni costituiscono gli unici oggetti che possono essere elaborati. Ai fini dell'elaborazione i gruppi di misure sono solo contenitori di partizioni. Il tipo specificato di elaborazione per il cubo viene propagato alle partizioni. L'elaborazione di un cubo e di un gruppo di misure viene risolta internamente nell'elaborazione di dimensioni e di partizioni.  
  
 Per ulteriori informazioni sulle opzioni di elaborazione, vedere [l'elaborazione di oggetti &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md), e [l'elaborazione di un modello multidimensionale &#40; Analysis Services &#41; ](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Nel codice seguente verrà eseguita un'elaborazione completa di tutti i cubi in un database specificato:  
  
```  
foreach (Cube cube in db.Cubes)  
             cube.Process(ProcessType.ProcessFull);  
     }  
```  
  
##  <a name="MG"></a>Oggetti MeasureGroup  
 Per amministrare o elaborare un gruppo di misure, programmare l'oggetto <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
### <a name="creating-dropping-and-finding-a-measuregroup"></a>Creazione, eliminazione e individuazione di un oggetto MeasureGroup  
 La gestione dei gruppi di misure è analoga a quella delle dimensioni e dei cubi. Per creare un oggetto <xref:Microsoft.AnalysisServices.MeasureGroup> sono necessari i passaggi seguenti:  
  
1.  Creazione dell'oggetto gruppo di misure e popolamento degli attributi di base.  
  
     Gli attributi di base includono gli attributi Nome, Modalità di archiviazione, Modalità di elaborazione, Misura predefinita e altri attributi del gruppo di misure.  
  
     Prima di creare un gruppo di misure, verificare che non esista. Nel codice di esempio seguente, se il gruppo di misure esiste viene eliminato e quindi ricreato.  
  
2.  Creazione delle misure del gruppo di misure. Per ogni misura creata, vengono assegnati gli attributi relativi a nome, funzione di aggregazione, colonna di origine e stringa di formato. È possibile assegnare inoltre altri attributi. Si noti che nel codice di esempio seguente il metodo CreateDataItem aggiunge la colonna allo schema.  
  
3.  Aggiunta delle dimensioni del gruppo di misure.  
  
4.  Le dimensioni vengono aggiunte alla raccolta corrente di dimensioni del gruppo di misure dalla raccolta di dimensioni del cubo padre. Non appena la dimensione viene inclusa nella raccolta di dimensioni del gruppo di misure, è possibile eseguire il mapping di una colonna chiave dalla tabella dei fatti alla dimensione in modo che il gruppo di misure possa essere visualizzato nella dimensione.  
  
     Nel codice di esempio seguente vedere le righe nella sezione "Mapping dimension and key column from fact table". Le dimensioni con ruoli multipli vengono implementate collegando chiavi surrogate differenti alla stessa dimensione con nomi diversi. A ogni dimensione con ruoli multipli (Date, Ship Date, Delivery Date) viene collegata una chiave surrogata diversa (OrderDateKey, ShipDateKey, DueDateKey). Tutte le chiavi provengono dalla tabella dei fatti FactInternetSales.  
  
5.  Aggiunta delle partizioni designate del gruppo di misure.  
  
     Nel codice di esempio seguente viene eseguito il wrapping della creazione della partizione in un metodo.  
  
6.  Aggiornamento del server tramite il metodo Update del gruppo di misure corrente.  
  
     Nel codice di esempio seguente tutti i gruppi di misure vengono aggiornati nel momento in cui viene aggiornato il cubo.  
  
 Nel codice di esempio seguente verrà creato il gruppo di misure InternetSales dell'esempio Adventure Works Analysis Services Project.  
  
```  
static void CreateInternetSalesMeasureGroup(Cube cube)  
{  
    // Create the Internet Sales measure group  
    Database db = cube.Parent;  
    MeasureGroup mg = cube.MeasureGroups.FindByName("Internet Sales");  
    if ( mg != null)  
       mg.Drop();  
    mg = cube.MeasureGroups.Add("Internet Sales");  
    mg.StorageMode = StorageMode.Molap;  
    mg.ProcessingMode = ProcessingMode.LazyAggregations;  
    mg.Type = MeasureGroupType.Sales;  
  
    #region Create measures  
  
    Measure meas;  
  
    meas = mg.Measures.Add("Internet Sales Amount");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    meas.FormatString = "Currency";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "SalesAmount");  
  
    meas = mg.Measures.Add("Internet Order Quantity");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    meas.FormatString = "#,#";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "OrderQuantity");  
  
    meas = mg.Measures.Add("Internet Unit Price");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    meas.FormatString = "Currency";  
    meas.Visible = false;  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "UnitPrice");  
  
    meas = mg.Measures.Add("Internet Total Product Cost");  
    meas.AggregateFunction = AggregationFunction.Sum;  
    //meas.MeasureExpression = "[Internet Total Product Cost] * [Average Rate]";  
    meas.FormatString = "Currency";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "TotalProductCost");  
  
    meas = mg.Measures.Add("Internet Order Count");  
    meas.AggregateFunction = AggregationFunction.Count;  
    meas.FormatString = "#,#";  
    meas.Source = CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "ProductKey");  
  
    #endregion  
  
    #region Create measure group dimensions  
  
    CubeDimension cubeDim;  
    RegularMeasureGroupDimension regMgDim;  
    ManyToManyMeasureGroupDimension mmMgDim;  
    MeasureGroupAttribute mgAttr;  
  
    //   Mapping dimension and key column from fact table  
    //      > select dimension and add it to the measure group  
    cubeDim = cube.Dimensions.GetByName("Date");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
  
    //      > add key column from dimension and map it with   
    //        the surrogate key in the fact table  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Date").ID);   // this is dimension key column  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "OrderDateKey"));   // this surrogate key in fact table  
  
    cubeDim = cube.Dimensions.GetByName("Ship Date");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Date").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "ShipDateKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Delivery Date");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Date").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "DueDateKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Customer");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Full Name").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "CustomerKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Product");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Product Name").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "ProductKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Source Currency");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Currency").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "CurrencyKey"));  
  
    cubeDim = cube.Dimensions.GetByName("Sales Reason");  
    mmMgDim = new ManyToManyMeasureGroupDimension();  
    mmMgDim.CubeDimensionID = cubeDim.ID;  
    mmMgDim.MeasureGroupID = cube.MeasureGroups.GetByName("Sales Reasons").ID;  
    mg.Dimensions.Add(mmMgDim);  
  
    cubeDim = cube.Dimensions.GetByName("Internet Sales Order Details");  
    regMgDim = new RegularMeasureGroupDimension(cubeDim.ID);  
    mg.Dimensions.Add(regMgDim);  
    mgAttr = regMgDim.Attributes.Add(cubeDim.Dimension.Attributes.GetByName("Sales Order Key").ID);  
    mgAttr.Type = MeasureGroupAttributeType.Granularity;  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "SalesOrderNumber"));  
    mgAttr.KeyColumns.Add(CreateDataItem(db.DataSourceViews[0], "FactInternetSales", "SalesOrderLineNumber"));  
  
    #endregion  
  
    #region Create partitions  
  
    CreateInternetSalesMeasureGroupPartitions( mg)  
  
    #endregion  
}  
```  
  
### <a name="processing-a-measure-group"></a>Elaborazione di un gruppo di misure  
 L'elaborazione di un gruppo di misure è semplice come l'utilizzo del metodo Process dell'oggetto <xref:Microsoft.AnalysisServices.MeasureGroup>. L'elaborazione di un gruppo di misure comporta l'elaborazione di tutte le partizioni che appartengono al gruppo di misure. L'elaborazione di un gruppo di misure viene risolta internamente nell'elaborazione di dimensioni e di partizioni. Vedere [l'elaborazione di una partizione](#ProcPart) in questo documento.  
  
 Per ulteriori informazioni sulle opzioni di elaborazione, vedere [l'elaborazione di oggetti &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md), e [l'elaborazione di un modello multidimensionale &#40; Analysis Services &#41; ](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Nel codice seguente verrà eseguita un'elaborazione completa di tutti i gruppi di misure di un cubo specificato:  
  
```  
static void FullProcessAllMeasureGroups(Cube cube)  
{  
    foreach (MeasureGroup mg in cube.MeasureGroups)  
        mg.Process(ProcessType.ProcessFull);  
}  
```  
  
##  <a name="Part"></a>Oggetti Partition  
 Per amministrare o elaborare una partizione, programmare un oggetto <xref:Microsoft.AnalysisServices.Partition>.  
  
### <a name="creating-dropping-and-finding-a-partition"></a>Creazione, eliminazione e individuazione di una partizione  
 Le partizioni sono oggetti semplici che possono essere creati in due passaggi.  
  
1.  Creazione dell'oggetto partizione e popolamento degli attributi di base.  
  
     Gli attributi di base sono Nome, Modalità di archiviazione, Origine partizione, Sezione e altri attributi della partizione. L'origine della partizione definisce l'istruzione SQL SELECT per la partizione corrente. La sezione è un'espressione MDX che specifica una tupla o un set che delimita una parte delle dimensioni del gruppo di misure padre contenute nella partizione corrente. Per le partizioni MOLAP, l'operazione di sezionamento viene determinata automaticamente ogni volta che la partizione viene elaborata.  
  
     Prima di creare una partizione, è necessario verificare che non esista. Nel codice di esempio seguente, se la partizione esiste viene eliminata e quindi ricreata.  
  
2.  Aggiornamento del server tramite il metodo Update della partizione corrente.  
  
     Nel codice di esempio seguente tutte le partizioni vengono aggiornate nel momento in cui viene aggiornato il cubo.  
  
 Nell'esempio di codice seguente vengono create le partizioni per il gruppo di misure "InternetSales".  
  
```  
static void CreateInternetSalesMeasureGroupPartitions(MeasureGroup mg)  
{  
    Partition part;  
    part = mg.Partitions.FindByName("Internet_Sales_184");  
    if ( part != null)  
       part.Drop();  
    part = mg.Partitions.Add("Internet_Sales_184");  
    part.StorageMode = StorageMode.Molap;  
    part.Source = new QueryBinding(db.DataSources[0].ID, "SELECT * FROM [dbo].[FactInternetSales] WHERE OrderDateKey <= '184'");  
    part.Slice = "[Date].[Calendar Year].&[2001]";  
    part.Annotations.Add("LastOrderDateKey", "184");  
  
    part = mg.Partitions.FindByName("Internet_Sales_549");  
    if ( part != null)  
       part.Drop();  
    part = mg.Partitions.Add("Internet_Sales_549");  
    part.StorageMode = StorageMode.Molap;  
    part.Source = new QueryBinding(db.DataSources[0].ID, "SELECT * FROM [dbo].[FactInternetSales] WHERE OrderDateKey > '184' AND OrderDateKey <= '549'");  
    part.Slice = "[Date].[Calendar Year].&[2002]";  
    part.Annotations.Add("LastOrderDateKey", "549");  
  
    part = mg.Partitions.FindByName("Internet_Sales_914");  
    if ( part != null)  
       part.Drop();  
    part = mg.Partitions.Add("Internet_Sales_914");  
    part.StorageMode = StorageMode.Molap;  
    part.Source = new QueryBinding(db.DataSources[0].ID, "SELECT * FROM [dbo].[FactInternetSales] WHERE OrderDateKey > '549' AND OrderDateKey <= '914'");  
    part.Slice = "[Date].[Calendar Year].&[2003]";  
    part.Annotations.Add("LastOrderDateKey", "914");  
}  
```  
  
###  <a name="ProcPart"></a>Elaborazione di una partizione  
 L'elaborazione di una dimensione è semplice come l'utilizzo del metodo Process dell'oggetto <xref:Microsoft.AnalysisServices.Partition>.  
  
 Per ulteriori informazioni sulle opzioni di elaborazione, vedere [l'elaborazione di oggetti &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md) e [l'elaborazione di un modello multidimensionale &#40; Analysis Services &#41; ](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Nell'esempio di codice seguente viene eseguita un'elaborazione completa di tutte le partizioni di un gruppo di misure specificato.  
  
```  
static void FullProcessAllPartitions(MeasureGroup mg)  
{  
    foreach (Partition part in mg.Partitions)  
        part.Process(ProcessType.ProcessFull);  
}  
```  
  
### <a name="merging-partitions"></a>Unione di partizioni  
 Per unione di partizioni si intende l'esecuzione di qualsiasi operazione che restituisce una partizione a partire da una o più partizioni.  
  
 L'unione di partizioni è un metodo dell'oggetto <xref:Microsoft.AnalysisServices.Partition>. Tale comando unisce i dati di una o più partizioni di origine in una partizione di destinazione ed elimina le partizioni di origine.  
  
 Le partizioni possono essere unite solo se soddisfano tutti i criteri seguenti:  
  
-   Appartenenza delle partizioni allo stesso gruppo di misure.  
  
-   Utilizzo della stessa modalità di archiviazione per le partizioni (MOLAP, HOLAP e ROLAP).  
  
-   Presenza delle partizioni nello stesso server. Le partizioni remote possono essere unite solo se si trovano nello stesso server.  
  
 Diversamente dalle versioni precedenti, in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non è necessario che tutte le partizioni di origine sono progettazione di aggregazioni identica.  
  
 Il set risultante di aggregazioni per la partizione di destinazione è lo stesso set di aggregazioni relativo allo stato precedente all'esecuzione del comando Merge.  
  
 Nell'esempio di codice seguente vengono unite tutte le partizioni di un gruppo di misure specificato. Le partizioni vengono unite nella prima partizione del gruppo di misure.  
  
```  
static void MergeAllPartitions(MeasureGroup mg)  
{  
    if (mg.Partitions.Count > 1)  
    {  
        Partition[] partArray = new Partition[mg.Partitions.Count - 1];  
        for (int i = 1; i < mg.Partitions.Count; i++)  
            partArray[i - 1] = mg.Partitions[i];  
        mg.Partitions[0].Merge(partArray);  
        //To have last changes in the server reflected in AMO  
        mg.Refresh();  
    }  
```  
  
##  <a name="AD"></a>Oggetti Aggregation  
 Per progettare un'aggregazione e applicarla a una o più a partizioni, programmare l'oggetto <xref:Microsoft.AnalysisServices.Aggregation>.  
  
### <a name="creating-and-dropping-aggregations"></a>Creazione ed eliminazione di aggregazioni  
 Le aggregazioni possono essere create e assegnate in modo semplice a gruppi di misure oppure a partizioni tramite il metodo DesignAggregations dell'oggetto <xref:Microsoft.AnalysisServices.AggregationDesign>. Il <xref:Microsoft.AnalysisServices.AggregationDesign> è un oggetto separato dalla partizione, il <xref:Microsoft.AnalysisServices.AggregationDesign> nell'oggetto è contenuto il <xref:Microsoft.AnalysisServices.MeasureGroup> oggetto. Le aggregazioni possono essere progettate in base a un livello specificato di ottimizzazione (compreso tra 0 e 100) o in base a un livello specificato di archiviazione (espresso in byte). Più partizioni possono utilizzare la stessa progettazione di aggregazioni.  
  
 Nell'esempio di codice seguente vengono create le aggregazioni per tutte le partizioni di un gruppo di misure specificato. Qualsiasi aggregazione esistente nelle partizioni viene eliminata.  
  
```  
static public String DesignAggregationsOnPartitions(MeasureGroup mg, double optimizationWanted, double maxStorageBytes)  
{  
    double optimization = 0;  
    double storage = 0;  
    long aggCount = 0;  
    bool finished = false;  
    AggregationDesign ad = null;  
    String aggDesignName;  
    String AggregationsDesigned = "";  
    aggDesignName = mg.AggregationPrefix + "_" + mg.Name;  
    ad = mg.AggregationDesigns.Add();  
    ad.Name = aggDesignName;  
    ad.InitializeDesign();  
    while ((!finished) && (optimization < optimizationWanted) && (storage < maxStorageBytes))  
    {  
        ad.DesignAggregations(out optimization, out storage, out aggCount, out finished);  
    }  
    ad.FinalizeDesign();  
    foreach (Partition part in mg.Partitions)  
    {  
        part.AggregationDesignID = ad.ID;  
        AggregationsDesigned += aggDesignName + " = " + aggCount.ToString() + " aggregations designed\r\n\tOptimization: " + optimization.ToString() + "/" + optimizationWanted.ToString() + "\n\r\tStorage: " + storage.ToString() + "/" + maxStorageBytes.ToString() + " ]\n\r";  
     }  
     return AggregationsDesigned;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Classi OLAP in AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-olap-classes.md)   
 [Architettura logica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)   
 [L'elaborazione di un modello multidimensionale &#40; Analysis Services &#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Installare dati di esempio e progetti per l'esercitazione di modellazione multidimensionale di Analysis Services](../../../analysis-services/install-sample-data-and-projects.md)  
  
  

