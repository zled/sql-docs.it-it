---
title: Classi di Data Mining AMO | Documenti Microsoft
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
- data mining [AMO]
- AMO, data mining
- Analysis Management Objects, data mining
ms.assetid: e4108825-b722-417c-9647-ab30ce35e549
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4eeb92697ce1a6a8475fa973a51ee6bdf9536b0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="amo-data-mining-classes"></a>Classi di data mining AMO
  Le classi di data mining consentono di creare, modificare, eliminare ed elaborare oggetti di dati mining. L'utilizzo di oggetti di data mining include la creazione di strutture e di modelli di data mining e l'elaborazione di tali modelli.  
  
 Per ulteriori informazioni su come configurare l'ambiente e sugli <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, e <xref:Microsoft.AnalysisServices.DataSourceView> degli oggetti, vedere [le classi fondamentali AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md).  
  
 Per la definizione degli oggetti nella libreria AMO (Analysis Management Objects), è necessario impostare alcune proprietà per ciascun oggetto in modo da configurare il contesto corretto. Per oggetti complessi, ad esempio oggetti OLAP e di data mining, è necessaria una codifica lunga e dettagliata.  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
-   [Oggetti MiningStructure](#MiningStructure)  
  
-   [Oggetti MiningModel](#MiningModel)  
  
 Nella figura seguente viene illustrata la relazione delle classi descritte in questo argomento.  
  
 ![Classi di data mining AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-dataminingclasses.gif "classi di data mining AMO")  
  
##  <a name="MiningStructure"></a>Oggetti MiningStructure  
 Una struttura di data mining rappresenta il contenitore per i modelli di data mining. La struttura definisce tutte le possibili colonne che i modelli di data mining possono utilizzare. Ogni modello di data mining definisce le proprie colonne dal set di colonne definite nella struttura.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.MiningStructure> semplice è costituito da informazioni di base, una vista origine dati, uno o più oggetti <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>, zero o più oggetti <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> e un oggetto <xref:Microsoft.AnalysisServices.MiningModelCollection>.  
  
 Le informazioni di base includono il nome e l'ID (identificatore interno) dell'oggetto <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
 Nell'oggetto <xref:Microsoft.AnalysisServices.DataSourceView> è contenuto il modello di data mining sottostante per la struttura di data mining.  
  
 L'oggetto <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> è costituito da colonne o attributi con valori singoli.  
  
 L'oggetto <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> è costituito da colonne o attributi con valori multipli per ciascun case.  
  
 Nell'oggetto <xref:Microsoft.AnalysisServices.MiningModelCollection> sono contenuti tutti i modelli di data mining compilati in base agli stessi dati.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.MiningStructure>, aggiungerlo all'oggetto <xref:Microsoft.AnalysisServices.MiningStructureCollection> del database e aggiornare l'oggetto <xref:Microsoft.AnalysisServices.MiningStructure> nel server tramite il metodo Update.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.MiningStructure>, è necessario eliminarlo tramite il metodo Drop dell'oggetto <xref:Microsoft.AnalysisServices.MiningStructure>. La rimozione di un oggetto <xref:Microsoft.AnalysisServices.MiningStructure> dalla raccolta non influisce sul server.  
  
 L'oggetto <xref:Microsoft.AnalysisServices.MiningStructure> può essere elaborato tramite il proprio metodo Process oppure nel momento in cui un oggetto padre elabora se stesso tramite il proprio metodo Process.  
  
### <a name="columns"></a>Colonne  
 Le colonne contengono i dati del modello e possono essere di tipi diversi, ovvero Key, Input, Predictable o InputPredictable a seconda dell'utilizzo. Le colonne stimabili rappresentano la destinazione della compilazione del modello di data mining.  
  
 In AMO le colonne a valore singolo sono note come oggetti <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>, mentre le colonne con valori multipli sono note come oggetti <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
#### <a name="scalarminingstructurecolumn"></a>ScalarMiningStructureColumn  
 Un oggetto <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> semplice è costituito da informazioni di base, dal tipo, dal contenuto e dall'associazione dati.  
  
 Le informazioni di base includono il nome e l'ID (identificatore interno) dell'oggetto <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
 Il tipo è rappresentato dal tipo di dati del valore, ovvero LONG, BOOLEAN, TEXT, DOUBLE o DATE.  
  
 Il contenuto indica al motore il modo in cui la colonna può essere modellata, in base ai valori possibili, ovvero Discrete, Continuous, Discretized, Ordered, Cyclical, Probability, Variance, StdDev, ProbabilityVariance, ProbabilityStdDev e Support, Key.  
  
 L'associazione dati consente di collegare la colonna di data mining con il modello di dati sottostante tramite un elemento della vista origine dati.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>, aggiungerlo all'oggetto <xref:Microsoft.AnalysisServices.MiningStructureCollection> padre e aggiornare l'oggetto <xref:Microsoft.AnalysisServices.MiningStructure> padre nel server tramite il metodo Update.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>, è necessario eliminarlo dalla raccolta dell'oggetto <xref:Microsoft.AnalysisServices.MiningStructure> padre e aggiornare l'oggetto <xref:Microsoft.AnalysisServices.MiningStructure> padre nel server tramite il metodo Update.  
  
#### <a name="tableminingstructurecolumn"></a>TableMiningStructureColumn  
 Un oggetto <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> semplice è costituito da informazioni di base e da colonne scalari.  
  
 Le informazioni di base includono il nome e l'ID (identificatore interno) dell'oggetto <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
 Le colonne scalari sono costituite dall'oggetto <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>, aggiungerlo alla raccolta <xref:Microsoft.AnalysisServices.MiningStructure> padre e aggiornare l'oggetto <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> padre nel server tramite il metodo Update.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>, è necessario eliminarlo dalla raccolta dell'oggetto <xref:Microsoft.AnalysisServices.MiningStructure> padre e aggiornare l'oggetto <xref:Microsoft.AnalysisServices.MiningStructure> padre nel server tramite il metodo Update.  
  
##  <a name="MiningModel"></a>Oggetti MiningModel  
 Un oggetto <xref:Microsoft.AnalysisServices.MiningModel> consente di scegliere le colonne della struttura e un algoritmo da utilizzare, nonché eventuali parametri specifici per ottimizzare il modello. Potrebbe essere necessario ad esempio definire nella stessa struttura di data mining diversi modelli di data mining che utilizzano gli stessi algoritmi, ma ignorare alcune colonne della struttura di data mining in un modello e utilizzarle come colonne di input in un altro modello e come colonne di input e di stima in un terzo modello. Queste operazioni possono risultare utili se si desidera considerare continua una colonna in un modello di data mining, ma discretizzata in un altro modello.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.MiningModel> semplice è costituito da informazioni di base, dalla definizione di algoritmo e da colonne.  
  
 Le informazioni di base includono il nome e l'ID (identificatore interno) del modello di data mining.  
  
 Una definizione di algoritmo fa riferimento a uno qualsiasi degli algoritmi standard disponibili in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oppure a qualsiasi algoritmo personalizzato abilitato nel server.  
  
 Le colonne sono costituite da una raccolta delle colonne utilizzate dall'algoritmo e dalla definizione del relativo utilizzo.  
  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.MiningModel>, aggiungerlo all'oggetto <xref:Microsoft.AnalysisServices.MiningModelCollection> del database e aggiornare l'oggetto <xref:Microsoft.AnalysisServices.MiningModel> nel server tramite il metodo Update.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.MiningModel>, è necessario eliminarlo tramite il metodo Drop dell'oggetto <xref:Microsoft.AnalysisServices.MiningModel>. La rimozione di un oggetto <xref:Microsoft.AnalysisServices.MiningModel> dalla raccolta non influisce sul server.  
  
 Dopo la creazione, un oggetto <xref:Microsoft.AnalysisServices.MiningModel> può essere elaborato tramite il proprio metodo Process oppure nel momento in cui un oggetto padre elabora se stesso tramite il proprio metodo Process.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Classi fondamentali AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)   
 [Oggetti di Data Mining di programmazione AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-data-mining-objects.md)   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Architettura logica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
