---
title: Programmazione di oggetti di Data Mining AMO | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- data mining [AMO]
- AMO, data mining
- Analysis Management Objects, data mining
ms.assetid: d27f58b9-91be-449c-8403-439aa6dd1ff9
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3c4c398dbda7bc898d62ea16122ccfba02ea7d5b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="programming-amo-data-mining-objects"></a>Programmazione di oggetti di data mining AMO
  La programmazione di oggetti di data mining tramite AMO è un'operazione estremamente semplice. Il primo passaggio consiste nella creazione del modello della struttura dei dati per supportare il progetto di data mining. Successivamente viene creato il modello di data mining che supporta l'algoritmo di data mining da utilizzare per stimare o individuare le relazioni non visibili sottostanti ai dati. Dopo avere creato il progetto di data mining, inclusi la struttura e gli algoritmi, è possibile elaborare i modelli di data mining per ottenere i modelli di cui è stato eseguito il training da utilizzare in un secondo momento durante l'esecuzione di query e di stime dall'applicazione client.  
  
 È importante tenere presente che AMO non è un modello per l'esecuzione di query, ma consente di gestire e amministrare le strutture e i modelli di data mining. Per eseguire query sui dati, utilizzare [allo sviluppo con ADOMD.NET](../../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md).  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
-   [Oggetti MiningStructure](#MiningStructure)  
  
-   [Oggetti MiningModel](#MiningModel)  
  
##  <a name="MiningStructure"></a>Oggetti MiningStructure  
 Una struttura di data mining è la definizione della struttura dei dati utilizzati per creare tutti i modelli di data mining. Una struttura di data mining contiene un'associazione a una vista origine dati definita nel database e contiene definizioni per tutte le colonne che partecipano ai modelli di data mining. In una struttura di data mining possono essere contenuti più modelli di data mining.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.MiningStructure>, sono necessari i passaggi seguenti:  
  
1.  Creazione dell'oggetto <xref:Microsoft.AnalysisServices.MiningStructure> e popolamento degli attributi di base. Gli attributi di base includono il nome dell'oggetto, l'ID dell'oggetto (identificazione interna) e l'associazione all'origine dati.  
  
2.  Creazione delle colonne per il modello. Le colonne possono essere scalari o definizioni di tabella.  
  
     Per ogni colonna è necessario definire un nome e un ID interno, un tipo, una definizione del contenuto e un'associazione.  
  
3.  Aggiornamento dell'oggetto <xref:Microsoft.AnalysisServices.MiningStructure> nel server tramite il metodo Update dell'oggetto.  
  
     Le strutture di data mining possono essere elaborate. Quando vengono elaborate, i modelli di data mining figlio vengono elaborati oppure ne viene eseguito nuovamente il training.  
  
 Nel codice di esempio seguente viene creata una struttura di data mining per prevedere le vendite in una serie temporale. Prima di eseguire il codice di esempio, assicurarsi che il database *db*, passato come parametro per `CreateSalesForecastingMiningStructure`, contiene `db.DataSourceViews[0]` un riferimento alla vista *dbo.vTimeSeries* nel [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)]database di esempio.  
  
```  
public static MiningStructure CreateSalesForecastingMiningStructure(Database db)  
{  
    MiningStructure ms = db.MiningStructures.FindByName("Forecasting Sales Structure");  
    if (ms != null)  
        ms.Drop();  
    ms = db.MiningStructures.Add("Forecasting Sales Structure", "Forecasting Sales Structure");  
    ms.Source = new DataSourceViewBinding(db.DataSourceViews[0].ID);  
  
    ScalarMiningStructureColumn amount = ms.Columns.Add("Amount", "Amount");  
    amount.Type = MiningStructureColumnTypes.Double;  
    amount.Content = MiningStructureColumnContents.Continuous;  
    amount.KeyColumns.Add("vTimeSeries", "Amount", OleDbType.Currency);  
  
    ScalarMiningStructureColumn modelRegion = ms.Columns.Add("Model Region", "Model Region");  
    modelRegion.IsKey = true;  
    modelRegion.Type = MiningStructureColumnTypes.Text;  
    modelRegion.Content = MiningStructureColumnContents.Key;  
    modelRegion.KeyColumns.Add("vTimeSeries", "ModelRegion", OleDbType.WChar, 56);  
  
    ScalarMiningStructureColumn qty = ms.Columns.Add("Quantity", "Quantity");  
    qty.Type = MiningStructureColumnTypes.Long;  
    qty.Content = MiningStructureColumnContents.Continuous;  
    qty.KeyColumns.Add("vTimeSeries", "Quantity", OleDbType.Integer);  
  
    ScalarMiningStructureColumn timeIndex = ms.Columns.Add("TimeIndex", "TimeIndex");  
    timeIndex.IsKey = true;  
    timeIndex.Type = MiningStructureColumnTypes.Long;  
    timeIndex.Content = MiningStructureColumnContents.KeyTime;  
    timeIndex.KeyColumns.Add("vTimeSeries", "TimeIndex", OleDbType.Integer);  
  
    ms.Update();  
    return ms;  
}  
```  
  
##  <a name="MiningModel"></a>Oggetti MiningModel  
 Un modello di data mining è un repository per tutte le colonne e le definizioni di colonna che verranno utilizzate in un algoritmo di data mining.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.MiningModel>, sono necessari i passaggi seguenti:  
  
1.  Creazione dell'oggetto <xref:Microsoft.AnalysisServices.MiningModel> e popolamento degli attributi di base.  
  
     Gli attributi di base includono il nome dell'oggetto, l'ID dell'oggetto (identificazione interna) e la specifica dell'algoritmo di data mining.  
  
2.  Aggiunta delle colonne al modello di data mining. Una delle colonne deve essere definita come chiave del case.  
  
3.  Aggiornamento dell'oggetto <xref:Microsoft.AnalysisServices.MiningModel> nel server tramite il metodo Update dell'oggetto.  
  
     Gli oggetti <xref:Microsoft.AnalysisServices.MiningModel> possono essere elaborati indipendentemente di altri modelli nell'oggetto padre <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
 Nel codice di esempio seguente viene creato un modello di previsione Microsoft Time Series basato sulla struttura di data mining "Forecasting Sales Structure":  
  
```  
public static MiningModel CreateSalesForecastingMiningModel(MiningStructure ms)  
{  
    if (ms.MiningModels.ContainsName("Sales Forecasting Model"))  
    {  
        ms.MiningModels["Sales Forecasting Model"].Drop();  
    }  
    MiningModel mm = ms.CreateMiningModel(true, "Sales Forecasting Model");  
    mm.Algorithm = MiningModelAlgorithms.MicrosoftTimeSeries;  
    mm.AlgorithmParameters.Add("PERIODICITY_HINT", "{12}");  
  
    MiningModelColumn amount = new MiningModelColumn();  
    amount.SourceColumnID = "Amount";  
    amount.Usage = MiningModelColumnUsages.Predict;  
  
    MiningModelColumn modelRegion = new MiningModelColumn();  
    modelRegion.SourceColumnID = "Model Region";  
    modelRegion.Usage = MiningModelColumnUsages.Key;  
  
    MiningModelColumn qty = new MiningModelColumn();  
    qty.SourceColumnID = "Quantity";  
    qty.Usage = MiningModelColumnUsages.Predict;  
  
    MiningModelColumn ti = new MiningModelColumn();  
    ti.SourceColumnID = "TimeIndex";  
    ti.Usage = MiningModelColumnUsages.Key;  
  
    mm.Update();  
    mm.Process(ProcessType.ProcessFull);  
    return mm;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Classi fondamentali AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Classi di Data Mining AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-data-mining-classes.md)   
 [Architettura logica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  

