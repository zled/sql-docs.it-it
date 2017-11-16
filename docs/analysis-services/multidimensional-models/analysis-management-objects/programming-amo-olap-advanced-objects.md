---
title: Oggetti avanzati OLAP in AMO programmazione | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
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
ms.assetid: b75f35a7-32df-4f22-983d-324aa98e15a9
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dedfe7e17d6f8fd0be0bb769b9891880a83b2eba
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="programming-amo-olap-advanced-objects"></a>Programmazione di oggetti avanzati OLAP in AMO
  In questo argomento vengono descritti i dettagli relativi alla programmazione di oggetti avanzati OLAP nella libreria AMO (Analysis Management Objects). In questo argomento sono incluse le sezioni seguenti:  
  
-   [Oggetti Action](#Action)  
  
-   [Oggetti KPI](#KPI)  
  
-   [Oggetti della prospettiva](#Persp)  
  
-   [Oggetti ProactiveCaching](#PC)  
  
-   [Oggetti Translation](#Transl)  
  
##  <a name="Action"></a>Oggetti Action  
 Le classi Action vengono utilizzate per creare una risposta attiva quando si visualizzano aree determinate del cubo. Gli oggetti di questo tipo possono essere definiti tramite AMO, ma vengono utilizzati dall'applicazione client che visualizza i dati. Sono disponibili azioni di tipo diverso, in base al quale è pertanto necessario crearle. Di seguito vengono indicati i diversi tipi di azione.  
  
-   Azioni drill-through, che restituiscono il set di righe che rappresenta i dati sottostanti delle celle selezionate del cubo in cui si verifica l'azione.  
  
-   Azioni report, che restituiscono un report di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] associato alla sezione selezionata del cubo in cui si verifica l'azione.  
  
-   Azioni standard, che restituiscono l'elemento dell'azione (URL, HTML, DataSet, RowSet e altri elementi) associato alla sezione selezionata del cubo in cui si verifica l'azione.  
  
 Per creare un oggetto azione, sono necessari i passaggi seguenti:  
  
1.  Creazione dell'oggetto azione derivato e popolamento degli attributi di base.  
  
     Gli attributi di base sono il tipo di azione, il tipo di destinazione o la sezione del cubo, l'area di destinazione o specifica del cubo in cui è disponibile l'azione, la didascalia e il punto in cui quest'ultima è un'espressione MDX.  
  
2.  Popolamento degli attributi specifici del tipo di azione.  
  
     Gli attributi sono diversi per i tre tipi di azioni. Per i parametri, vedere l'esempio di codice riportato di seguito.  
  
3.  Aggiunta dell'azione alla raccolta di cubi e aggiornamento del cubo. L'azione non è un oggetto aggiornabile.  
  
 Per eseguire il test dell'azione, è necessaria un'applicazione diversa. È possibile eseguire il test dell'azione in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], In primo luogo, è necessario installare [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] esempi, vedere [l'elaborazione di un modello multidimensionale &#40; Analysis Services &#41; ](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Nel codice di esempio seguente vengono replicate tre azioni diverse dell'esempio Adventure Works Analysis Services Project. È possibile differenziare le azioni poiché quelle introdotte tramite l'esempio seguente iniziano con "My".  
  
```  
static public void CreateActions(Cube cube)  
{  
    #region Adding a drillthrough action  
    // Verify That action exists and drop it  
    if (cube.Actions.ContainsName("My Reseller Details"))  
        cube.Actions.Remove("My Drillthrough Action",true);  
  
    //Create a Drillthrough action  
    DrillThroughAction dtaction = new DrillThroughAction("My Reseller Details", "My Drillthrough Action");  
  
    //Define the Action  
    dtaction.Type = ActionType.DrillThrough;  
    dtaction.TargetType = ActionTargetType.Cells;  
    dtaction.Target = "MeasureGroupMeasures(\"Reseller Sales\")";  
    dtaction.Caption = "My Drillthrough...";  
    dtaction.CaptionIsMdx = false;  
  
    #region create drillthrough action specifics  
    //Adding Drillthrough columns  
    //Adding Measure columns to the drillthrough  
    MeasureGroup mg = cube.MeasureGroups.FindByName("Reseller Sales");  
    MeasureBinding mb1 = new MeasureBinding();  
    mb1.MeasureID = mg.Measures.FindByName( "Reseller Sales Amount").ID;  
    dtaction.Columns.Add(mb1);  
  
    MeasureBinding mb2 = new MeasureBinding();  
    mb2.MeasureID = mg.Measures.FindByName("Reseller Order Quantity").ID;  
    dtaction.Columns.Add(mb2);  
  
    MeasureBinding mb3 = new MeasureBinding();  
    mb3.MeasureID = mg.Measures.FindByName("Reseller Unit Price").ID;  
    dtaction.Columns.Add(mb3);  
  
    //Adding Dimension Columns to the drillthrough  
    CubeAttributeBinding cb1 = new CubeAttributeBinding();  
    cb1.CubeID = cube.ID;  
    cb1.CubeDimensionID = cube.Dimensions.FindByName("Reseller").ID;  
    cb1.AttributeID = "Reseller Name";  
    cb1.Type = AttributeBindingType.All;  
    dtaction.Columns.Add(cb1);  
  
    CubeAttributeBinding cb2 = new CubeAttributeBinding();  
    cb2.CubeID = cube.ID;  
    cb2.CubeDimensionID = cube.Dimensions.FindByName("Product").ID;  
    cb2.AttributeID = "Product Name";  
    cb2.Type = AttributeBindingType.All;  
    dtaction.Columns.Add(cb2);  
    #endregion  
  
    //Add the defined action to the cube  
    cube.Actions.Add(dtaction);  
    #endregion  
  
    #region Adding a Standard action  
    // Verify That action exists and drop it  
    if (cube.Actions.ContainsName("My City Map"))  
        cube.Actions.Remove("My Action", true);  
  
    //Create a Drillthrough action  
    StandardAction stdaction = new StandardAction("My City Map", "My Action");  
  
    //Define the Action  
    stdaction.Type = ActionType.Url;  
    stdaction.TargetType = ActionTargetType.AttributeMembers;  
    stdaction.Target = "[Geography].[City]";  
    stdaction.Caption = "\"My View Map for \" + [Geography].[City].CurrentMember.Member_Caption + \"...\"";  
    stdaction.CaptionIsMdx = true;  
  
    #region create standard action specifics  
    stdaction.Expression = "\"http://maps.msn.com/home.aspx?plce1=\" + " +  
        "[Geography].[City].CurrentMember.Name + \",\" + " +  
        "[Geography].[State-Province].CurrentMember.Name + \",\" + " +  
        "[Geography].[Country].CurrentMember.Name + " +  
        "\"&regn1=\" + " +  
        "Case " +  
            "When [Geography].[Country].CurrentMember Is " +  
                    "[Geography].[Country].&[Australia] " +  
                "Then \"3\" " +  
            "When [Geography].[Country].CurrentMember Is " +  
                    "[Geography].[Country].&[Canada] " +  
                "Or [Geography].[Country].CurrentMember Is " +  
                    "[Geography].[Country].&[United States] " +  
                "Then \"0\" " +  
                "Else \"1\" " +  
        "End ";  
    #endregion  
  
    //Add the defined action to the cube  
    cube.Actions.Add(stdaction);  
  
    #endregion  
  
    #region Adding a Reporting action  
    // Verify That action exists and drop it  
    if (cube.Actions.ContainsName("My Sales Reason Comparisons"))  
        cube.Actions.Remove("My Report Action", true);  
  
    //Create a Report action  
    ReportAction rsaction = new ReportAction("My Sales Reason Comparisonsp", "My Report Action");  
  
    //Define the Action  
    rsaction.Type = ActionType.Report;  
    rsaction.TargetType = ActionTargetType.AttributeMembers;  
    rsaction.Target = "[Product].[Category]";  
    rsaction.Caption = "\"My Sales Reason Comparisons for \" + [Product].[Category].CurrentMember.Member_Caption + \"...\"";  
    rsaction.CaptionIsMdx = true;  
  
    #region create Report action specifics  
    rsaction.ReportServer = "MyRSSamplesServer";  
    rsaction.Path = "ReportServer?/AdventureWorks Sample Reports/Sales Reason Comparisons";  
    rsaction.ReportParameters.Add("ProductCategory", "UrlEscapeFragment( [Product].[Category].CurrentMember.UniqueName )");  
    rsaction.ReportFormatParameters.Add("rs:Command", "Render");  
    rsaction.ReportFormatParameters.Add("rs:Renderer", "HTML5");  
    #endregion  
  
    //Add the defined action to the cube  
    cube.Actions.Add(rsaction);  
  
    #endregion  
}  
```  
  
##  <a name="KPI"></a>Oggetti KPI  
 Un indicatore di prestazioni chiave (KPI) è costituito da una raccolta di calcoli associati a un gruppo di misure in un cubo e utilizzati per valutare il successo aziendale. Gli oggetti <xref:Microsoft.AnalysisServices.Kpi> possono essere definiti in AMO, ma vengono utilizzati dall'applicazione client che visualizza i dati.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Kpi>, sono necessari i passaggi seguenti:  
  
1.  Creazione dell'oggetto <xref:Microsoft.AnalysisServices.Kpi> e popolamento degli attributi di base.  
  
     Gli attributi di base includono Descrizione, Cartella di visualizzazione, Gruppo di misure associato e Valore. L'attributo Cartella di visualizzazione indica all'applicazione client la posizione dell'indicatore KPI in modo che l'utente finale sia in grado di individuarlo. L'attributo Gruppo di misure associato indica il gruppo di misure in cui è necessario fare riferimento a tutti i calcoli MDX. L'attributo Valore indica il valore effettivo dell'indicatore di prestazioni come espressione MDX.  
  
2.  Definizione degli indicatori KPI Obiettivo, Stato e Tendenza.  
  
     Gli indicatori sono espressioni MDX con valore compreso tra -1 e 1. L'intervallo di valori per gli indicatori viene tuttavia definito dall'applicazione per la visualizzazione.  
  
3.  Quando si visualizzano gli indicatori KPI in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], i valori minori di -1 vengono considerati come -1, mentre quelli maggiori di 1 vengono considerati come 1.  
  
4.  Definizione di immagini grafiche.  
  
     Le immagini grafiche sono valori stringa utilizzati come riferimento nell'applicazione client per identificare il set corretto di immagini da visualizzare. Le stringhe relative alle immagini grafiche definiscono inoltre il comportamento della funzione di visualizzazione. In genere l'intervallo è suddiviso in un numero dispari di stati, da negativo a buono, e a ogni stato viene assegnata un'immagine del set.  
  
     Se si utilizza [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] per visualizzare gli indicatori KPI, a seconda dei nomi l'intervallo relativo agli indicatori è suddiviso in tre oppure in cinque stati. Sono inoltre presenti nomi in cui l'intervallo è invertito, ovvero il valore -1 indica un risultato buono, mentre il valore 1 indica un risultato negativo. In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] i tre stati compresi nell'intervallo sono i seguenti:  
  
    -   Errato = da 1 a 0,5  
  
    -   OK = da -0,4999 a 0,4999  
  
    -   Buono = da 0,50 a 1  
  
     In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] i cinque stati compresi nell'intervallo sono i seguenti:  
  
    -   Negativo = da -1 a -0,75  
  
    -   A rischio = da -0,7499 a -0,25  
  
    -   OK = da -0,2499 a 0,2499  
  
    -   In aumento = da 0,25 a 0,7499  
  
    -   Buono = da 0,75 a 1  
  
 Nella tabella seguente vengono elencati l'utilizzo, il nome e il numero di stati associati all'immagine.  
  
|Utilizzo immagine|Nome immagine|Numero di stati|  
|-----------------|----------------|----------------------|  
|Stato|Forme|3|  
|Stato|Semaforo|3|  
|Stato|Segnali stradali|3|  
|Stato|Misuratore|3|  
|Stato|Misuratore capovolto|5|  
|Stato|Termometro|3|  
|Stato|Cilindro|3|  
|Stato|Smile|3|  
|Stato|Freccia di varianza|3|  
|Tendenza|Freccia standard|3|  
|Tendenza|Freccia di stato|3|  
|Tendenza|Freccia di stato capovolta|5|  
|Tendenza|Smile|3|  
  
1.  Aggiunta dell'indicatore KPI alla raccolta di cubi e aggiornamento del cubo poiché l'indicatore KPI non è un oggetto aggiornabile.  
  
 Per eseguire il test dell'indicatore KPI, è necessaria un'applicazione diversa. È possibile eseguire il test dell'indicatore KPI in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
 Nel codice di esempio seguente viene creato un indicatore KPI nella cartella "Financial Perpective/Grow Revenue" per il cubo Adventure Works incluso nell'esempio Adventure Works Analysis Services Project.  
  
```  
static public void CreateKPIs(Cube cube)  
{  
    Kpi kpi = cube.Kpis.Add("My Internet Revenue", "My Internet Revenue");  
    kpi.Description = "(My) Revenue achieved through direct sales via Interner";  
    kpi.DisplayFolder = "\\Financial Perspective\\Grow Revenue";  
    kpi.AssociatedMeasureGroupID = "Internet Sales";  
    kpi.Value = "[Measures].[Internet Sales Amount]";  
    #region Goal  
    kpi.Goal = "Case" +  
               "     When IsEmpty" +  
               "          (" +  
               "            ParallelPeriod" +  
               "            (" +  
               "              [Date].[Fiscal Time].[Fiscal Year]," +  
               "              1," +  
               "              [Date].[Fiscal Time].CurrentMember" +  
               "            )" +  
               "          )" +   
               "     Then [Measures].[Internet Sales Amount]" +  
               "     Else 1.10 *" +  
               "          (" +  
               "            [Measures].[Internet Sales Amount]," +  
               "            ParallelPeriod" +  
               "            (" +  
               "              [Date].[Fiscal Time].[Fiscal Year]," +  
               "              1," +  
               "              [Date].[Fiscal Time].CurrentMember" +  
               "            )" +  
               "          ) " +  
               " End";  
    #endregion  
    #region Status  
    kpi.Status = "Case" +  
                 "   When KpiValue( \"Internet Revenue\" ) / KpiGoal ( \"Internet Revenue\" ) >= .95 " +  
                 "   Then 1 " +  
                 "   When KpiValue( \"Internet Revenue\" ) / KpiGoal ( \"Internet Revenue\" ) <  .95 " +  
                 "        And  " +  
                 "        KpiValue( \"Internet Revenue\" ) / KpiGoal ( \"Internet Revenue\" ) >= .85 " +  
                 "   Then 0 " +  
                 "   Else -1 " +  
                 "End";  
    #endregion  
    #region Trend  
    kpi.Trend = "Case " +  
                "    When VBA!Abs " +  
                "         ( " +  
                "           KpiValue( \"Internet Revenue\" ) -  " +  
                "           ( " +  
                "             KpiValue ( \"Internet Revenue\" ), " +  
                "             ParallelPeriod " +  
                "             (  " +  
                "               [Date].[Fiscal Time].[Fiscal Year], " +  
                "               1, " +  
                "               [Date].[Fiscal Time].CurrentMember " +  
                "             ) " +  
                "           ) / " +  
                "           ( " +  
                "             KpiValue ( \"Internet Revenue\" ), " +  
                "             ParallelPeriod " +  
                "             (  " +  
                "               [Date].[Fiscal Time].[Fiscal Year], " +  
                "               1, " +  
                "               [Date].[Fiscal Time].CurrentMember " +  
                "             ) " +  
                "           )   " +  
                "         ) <=.02  " +  
                "    Then 0 " +  
                "    When KpiValue( \"Internet Revenue\" ) -  " +  
                "         ( " +  
                "           KpiValue ( \"Internet Revenue\" ), " +  
                "           ParallelPeriod " +  
                "           (  " +  
                "             [Date].[Fiscal Time].[Fiscal Year], " +  
                "             1, " +  
                "             [Date].[Fiscal Time].CurrentMember " +  
                "           ) " +  
                "         ) / " +  
                "         ( " +  
                "           KpiValue ( \"Internet Revenue\" ), " +  
                "           ParallelPeriod " +  
                "           (  " +  
                "             [Date].[Fiscal Time].[Fiscal Year], " +  
                "             1, " +  
                "             [Date].[Fiscal Time].CurrentMember " +  
                "           ) " +  
                "         )  >.02 " +  
                "    Then 1 " +  
                "    Else -1 " +  
                "End";  
    #endregion  
    kpi.TrendGraphic = "Standard Arrow";  
    kpi.StatusGraphic = "Cylinder";  
}.  
```  
  
##  <a name="Persp"></a>Oggetti della prospettiva  
 Gli oggetti <xref:Microsoft.AnalysisServices.Perspective> possono essere definiti in AMO, ma vengono utilizzati dall'applicazione client che visualizza i dati.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Perspective>, sono necessari i passaggi seguenti:  
  
1.  Creazione dell'oggetto <xref:Microsoft.AnalysisServices.Perspective> e popolamento degli attributi di base.  
  
     Gli attributi di base includono Nome, Misura predefinita, Descrizione e dalle annotazioni.  
  
2.  Aggiunta di tutti gli oggetti dal cubo padre che deve essere visualizzato dall'utente finale.  
  
     Aggiunta di dimensioni del cubo (attributi e gerarchie), gruppi di misure (misura e gruppi di misure), azioni, indicatori di prestazioni chiave (KPI) e calcoli.  
  
3.  Aggiunta della prospettiva alla raccolta di cubi e aggiornamento del cubo poiché la prospettiva non è un oggetto aggiornabile.  
  
 Per eseguire il test della prospettiva, è necessaria un'applicazione diversa. È possibile eseguire il test della prospettiva in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
 Nell'esempio di codice seguente viene creata una prospettiva denominata "Direct Sales" per il cubo specificato.  
  
```  
static public void CreatePerspectives(Cube cube)  
{  
    Perspective perspective = cube.Perspectives.Add("Direct Sales", "Direct Sales");  
    CubeDimension dim1 = cube.Dimensions.GetByName("Date");  
    PerspectiveDimension pdim1 = perspective.Dimensions.Add(dim1.DimensionID);  
    pdim1.Attributes.Add("Date");  
    pdim1.Attributes.Add("Calendar Year");  
    pdim1.Attributes.Add("Fiscal Year");  
    pdim1.Attributes.Add("Calendar Quarter");  
    pdim1.Attributes.Add("Fiscal Quarter");  
    pdim1.Attributes.Add("Calendar Month Number");  
    pdim1.Attributes.Add("Fiscal Month Number");  
    pdim1.Hierarchies.Add("Calendar Time");  
    pdim1.Hierarchies.Add("Fiscal Time");  
  
    CubeDimension dim2 = cube.Dimensions.GetByName("Product");  
    PerspectiveDimension pdim2 = perspective.Dimensions.Add(dim2.DimensionID);  
    pdim2.Attributes.Add("Product Name");  
    pdim2.Attributes.Add("Product Line");  
    pdim2.Attributes.Add("Model Name");  
    pdim2.Attributes.Add("List Price");  
    pdim2.Attributes.Add("Size");  
    pdim2.Attributes.Add("Weight");  
    pdim2.Hierarchies.Add("Product Model Categories");  
    pdim2.Hierarchies.Add("Product Categories");  
  
    PerspectiveMeasureGroup pmg = perspective.MeasureGroups.Add("Internet Sales");  
    pmg.Measures.Add("Internet Sales Amount");  
    pmg.Measures.Add("Internet Order Quantity");  
    pmg.Measures.Add("Internet Unit Price");  
  
    pmg = perspective.MeasureGroups.Add("Reseller Sales");  
    pmg.Measures.Add("Reseler Sales Amount");  
    pmg.Measures.Add("Reseller Order Quantity");  
    pmg.Measures.Add("Reseller Unit Price");  
  
    PerspectiveAction pact = perspective.Actions.Add("Drillthrough Action");  
  
    PerspectiveKpi pkpi = perspective.Kpis.Add("Internet Revenue");  
    Cube.Update();  
}  
```  
  
##  <a name="PC"></a>Oggetti ProactiveCaching  
 Gli oggetti <xref:Microsoft.AnalysisServices.ProactiveCaching> possono essere definiti in AMO.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching>, sono necessari i passaggi seguenti:  
  
1.  Creazione dell'oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
     Non è presente alcun attributo di base da definire.  
  
2.  Aggiunta delle specifiche relative alla cache.  
  
|Specifica|Description|  
|-------------------|-----------------|  
|AggregationStorage|Tipo di archiviazione per le aggregazioni.<br /><br /> Si applica solo alla partizione. Dimensione deve essere **regolare.**|  
|SilenceInterval|Periodo minimo di tempo durante il quale la cache esiste prima che venga avviato il processo di imaging MOLAP.|  
|Latenza|Periodo di tempo tra la prima notifica e il momento in cui le immagini MOLAP vengono eliminate.|  
|SilenceOverrideInterval|Periodo di tempo successivo a una notifica iniziale dopo il quale il processo di imaging MOLAP viene avviato in modo incondizionato.|  
|ForceRebuildInterval|Periodo di tempo (a partire dal momento in cui un'immagine MOLAP aggiornata viene eliminata) dopo il quale il processo di imaging MOLAP viene avviato in modo incondizionato (senza alcun notifica).|  
|OnlineMode|Momento in cui l'immagine MOLAP è disponibile.<br /><br /> Può essere **immediato** o **OnCacheComplete**.|  
  
1.  Aggiunta dell'oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching> alla raccolta padre. Sarà necessario aggiornare la raccolta padre poiché <xref:Microsoft.AnalysisServices.ProactiveCaching> non è un oggetto aggiornabile.  
  
 Nell'esempio di codice seguente viene creato un oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching> in tutte le partizioni dal gruppo di misure Internet Sales nel cubo Adventure Works di un database specificato.  
  
```  
static public void SetProactiveCachingSettings(Database db)  
{  
    ProactiveCaching pc;  
    if (db.Cubes.ContainsName("Adventure Works") && db.Cubes.FindByName("Adventure Works").MeasureGroups.ContainsName("Internet Sales"))  
    {  
        ProactiveCachingTablesBinding pctb;  
        TableNotification tn;  
  
        MeasureGroup mg = db.Cubes.FindByName("Adventure Works").MeasureGroups.FindByName("Internet Sales");  
        foreach(Partition part in mg.Partitions)  
        {  
            pc = new ProactiveCaching();  
            pc.AggregationStorage = ProactiveCachingAggregationStorage.MolapOnly;  
            pc.SilenceInterval = TimeSpan.FromSeconds(10);  
            pc.Latency = TimeSpan.FromSeconds(-1);  
            pc.SilenceOverrideInterval = TimeSpan.FromMinutes(10);  
            pc.ForceRebuildInterval = TimeSpan.FromSeconds(-1);  
            pc.Enabled = true;  
            pc.OnlineMode = ProactiveCachingOnlineMode.OnCacheComplete;  
            pctb = new ProactiveCachingTablesBinding();  
            pctb.NotificationTechnique = NotificationTechnique.Server;  
            tn = new TableNotification("[FactInternetSales]", "dbo");  
            pctb.TableNotifications.Add( tn);  
            pc.Source = pctb;  
  
            part.ProactiveCaching = pc;  
            part.Update();  
        }  
    }  
}  
```  
  
##  <a name="Transl"></a>Oggetti Translation  
 Gli oggetti Translation possono essere definiti in AMO, ma vengono utilizzati dall'applicazione client che visualizza i dati. La codifica di oggetti di questo tipo è un'operazione semplice. Le traduzioni per le didascalie degli oggetti vengono fornite da coppie costituite da un identificatore delle impostazioni locali e da una didascalia tradotta. Per ogni didascalia è possibile abilitare più traduzioni. Le traduzioni possono essere fornite per la maggior parte degli oggetti di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], ad esempio dimensioni, attributi gerarchie, cubi, gruppi di misure, misure e altri oggetti.  
  
 Nell'esempio di codice seguente viene fornita la traduzione in spagnolo per il nome dell'attributo Product Name.  
  
```  
static public void CreateTranslations(Database db)  
{  
    //Spanish Tranlations for Product Category in Product Dimension  
    Dimension dim = db.Dimensions["Product"];  
    DimensionAttribute atr = dim.Attributes["Product Name"];  
    Translation tran = atr.Translations.Add(3082);  
    tran.Caption = "Nombre Producto";  
  
    dim.Update(UpdateOptions.ExpandFull);  
  
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
  
  

