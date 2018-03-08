---
title: Classi OLAP in AMO | Documenti Microsoft
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Management Objects, OLAP
- OLAP [AMO]
- AMO, OLAP
ms.assetid: 397509b7-a4fb-40de-aa30-c66dc9ed2105
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 609958fd81ee7c703d7608f9a353c15658c1528b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="amo-olap-classes"></a>Classi OLAP di AMO
  Le classi OLAP della libreria AMO (Analysis Management Objects) consentono di creare, modificare, eliminare ed elaborare cubi, dimensioni e oggetti correlati, ad esempio indicatori di prestazioni chiave (KPI), azioni e memorizzazione nella cache attiva.  
  
 Per ulteriori informazioni sull'impostazione di ambiente di programmazione AMO, come origini per stabilire una connessione con un server, l'accesso a un database o la definizione dei dati e viste origine dati, vedere [le classi fondamentali AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md).  
  
 In questo argomento sono incluse le sezioni seguenti:  
  
-   [Oggetti Dimension](#Dimensions)  
  
-   [Oggetti del cubo](#Cubes)  
  
-   [Oggetti MeasureGroup](#MeasureGroups)  
  
-   [Oggetti Partition](#Partition)  
  
-   [Oggetti AggregationDesign](#AggregationDesign)  
  
-   [Oggetti Aggregation](#Aggregation)  
  
-   [Oggetti Action](#Action)  
  
-   [Oggetti KPI](#KPI)  
  
-   [Oggetti della prospettiva](#Perspective)  
  
-   [Oggetti Translation](#Translation)  
  
-   [Oggetti ProactiveCaching](#ProactiveCaching)  
  
 Nella figura seguente viene illustrata la relazione delle classi descritte in questo argomento.  
  
 ![Classi OLAP in AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-olapclasses.gif "classi OLAP in AMO")  
  
## <a name="basic-classes"></a>Classi di base  
  
###  <a name="Dimensions"></a> Oggetti Dimension  
 Per creare una dimensione, aggiungerla alla raccolta di dimensioni del database padre e aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Dimension> nel server tramite il metodo Update.  
  
 Per rimuovere una dimensione, eliminarla tramite il metodo Drop dell'oggetto <xref:Microsoft.AnalysisServices.Dimension>. La rimozione di un oggetto <xref:Microsoft.AnalysisServices.Dimension> dalla raccolta di dimensioni del database tramite il metodo Remove non ne provoca l'eliminazione dal server, ma solo dal modello a oggetti AMO.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.Dimension> può essere elaborato dopo che è stato creato. L'oggetto <xref:Microsoft.AnalysisServices.Dimension> può essere elaborato tramite il proprio metodo Process oppure con il metodo Process dell'oggetto padre durante l'elaborazione di quest'ultimo.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Dimension> in <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Cubes"></a> Oggetti del cubo  
 Per creare un cubo, aggiungerlo alla raccolta di cubi del database, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Cube> nel server tramite il metodo Update. Il metodo Update del cubo può includere il parametro UpdateOptions.ExpandFull che garantisce l'aggiornamento nel server di tutti gli oggetti del cubo che sono stati modificati.  
  
 Per rimuovere un cubo, eliminarlo tramite il metodo Drop dell'oggetto <xref:Microsoft.AnalysisServices.Cube>. La rimozione di un cubo dalla raccolta non influisce sul server.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.Cube> può essere elaborato dopo che è stato creato. L'oggetto <xref:Microsoft.AnalysisServices.Cube> può essere elaborato tramite il proprio metodo Process oppure nel momento in cui un oggetto padre elabora se stesso tramite il proprio metodo Process.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Cube> in <xref:Microsoft.AnalysisServices>.  
  
###  <a name="MeasureGroups">Oggetti MeasureGroup</a>  
 Per creare un gruppo di misure, aggiungerlo alla raccolta dei gruppi di misure del cubo, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.MeasureGroup> nel server tramite il relativo metodo Update. Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.MeasureGroup>, utilizzare il relativo metodo Drop.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.MeasureGroup> può essere elaborato dopo che è stato creato. L'oggetto <xref:Microsoft.AnalysisServices.MeasureGroup> può essere elaborato tramite il proprio metodo Process oppure nel momento in cui un oggetto padre elabora se stesso tramite il proprio metodo Process.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.MeasureGroup> in <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Partition">Oggetti Partition</a>  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Partition>, aggiungerlo alla raccolta di partizioni del gruppo di misure padre, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Partition> nel server tramite il metodo Update. Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Partition>, utilizzare il metodo Drop.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Partition> in <xref:Microsoft.AnalysisServices>.  
  
###  <a name="AggregationDesign">Oggetti AggregationDesign</a>  
 Le progettazioni delle aggregazioni vengono realizzate tramite il metodo AggregationDesign da un oggetto <xref:Microsoft.AnalysisServices.AggregationDesign>.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.AggregationDesign> in <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Aggregation">Oggetti Aggregation</a>  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Aggregation>, aggiungerlo alla raccolta di progettazioni delle aggregazioni del gruppo di misure padre, quindi aggiornare l'oggetto gruppo di misure padre nel server tramite il metodo Update. Per rimuovere un'aggregazione da <xref:Microsoft.AnalysisServices.AggregationCollection>, utilizzare il metodo Remove o RemoveAt.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Aggregation> in <xref:Microsoft.AnalysisServices>.  
  
## <a name="advanced-classes"></a>Classi avanzate  
 Oltre a compilare ed esplorare un cubo, le classi avanzate consentono di utilizzare le funzionalità OLAP. Di seguito vengono riportate alcune classi avanzate e i relativi vantaggi:  
  
-   Le classi Action vengono utilizzate per creare una risposta attiva quando si visualizzano aree determinate del cubo.  
  
-   Gli indicatori di prestazioni chiave (KPI) consentono di eseguire analisi di confronto tra valori di dati.  
  
-   Le prospettive forniscono viste selezionate di un unico cubo, in modo che gli utenti possano visualizzare esclusivamente gli elementi che ritengono più importanti.  
  
-   Le conversioni consentono di personalizzare il cubo in base alle impostazioni locali dell'utente.  
  
-   Le classi di memorizzazione nella cache attiva consentono di raggiungere un compromesso tra le prestazioni ottimizzate dell'archiviazione MOLAP e l'immediatezza dell'archiviazione ROLAP e supportano l'elaborazione pianificata delle partizioni.  
  
 AMO viene utilizzato per impostare le definizioni per questo comportamento ottimizzato, ma l'esperienza effettiva viene definita dall'esplorazione del client in cui tali miglioramenti sono implementati.  
  
###  <a name="Action">Oggetti Action</a>  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Action>, aggiungerlo alla raccolta di azioni del cubo, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Cube> nel server tramite il metodo Update. Il metodo Update del cubo può includere il parametro UpdateOptions.ExpandFull che garantisce l'aggiornamento nel server di tutti gli oggetti del cubo che sono stati modificati.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Action>, è necessario innanzitutto rimuoverlo dalla raccolta e successivamente aggiornare il cubo padre.  
  
 Prima che l'oggetto Action possa essere utilizzato dal client, il cubo deve essere aggiornato ed elaborato.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Action> in <xref:Microsoft.AnalysisServices>.  
  
###  <a name="KPI"></a> Oggetti KPI  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Kpi>, aggiungerlo alla raccolta di indicatori di prestazioni chiave del cubo, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Cube> nel server tramite il metodo Update. Il metodo Update del cubo può includere il parametro UpdateOptions.ExpandFull che garantisce l'aggiornamento nel server di tutti gli oggetti del cubo che sono stati modificati.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Kpi>, è necessario innanzitutto rimuoverlo dalla raccolta e successivamente aggiornare il cubo padre.  
  
 Per utilizzare l'indicatore di prestazioni chiave, un cubo deve essere aggiornato ed elaborato.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Kpi> in <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Perspective">Oggetti della prospettiva</a>  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Perspective>, aggiungerlo alla raccolta di prospettive del cubo, quindi aggiornare l'oggetto <xref:Microsoft.AnalysisServices.Cube> nel server tramite il metodo Update. Il metodo Update del cubo può includere il parametro UpdateOptions.ExpandFull che garantisce l'aggiornamento nel server di tutti gli oggetti del cubo che sono stati modificati.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Perspective>, è necessario innanzitutto rimuoverlo dalla raccolta e successivamente aggiornare il cubo padre.  
  
 Per utilizzare la prospettiva, è necessario aggiornare ed elaborare un cubo.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Perspective> in <xref:Microsoft.AnalysisServices>.  
  
###  <a name="Translation">Oggetti Translation</a>  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.Translation>, aggiungerlo alla raccolta di conversioni dell'oggetto desiderato e successivamente aggiornare l'oggetto padre principale più vicino nel server tramite il metodo Update. Il metodo Update dell'oggetto padre più vicino può includere il parametro UpdateOptions.ExpandFull che garantisce l'aggiornamento nel server di tutti gli oggetti del cubo che sono stati modificati.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.Translation>, è necessario innanzitutto rimuoverlo dalla raccolta e successivamente aggiornare l'oggetto padre più vicino.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.Translation> in <xref:Microsoft.AnalysisServices>.  
  
###  <a name="ProactiveCaching">Oggetti ProactiveCaching</a>  
 Per creare un oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching>, aggiungerlo alla raccolta di oggetti di memorizzazione nella cache attiva della dimensione o partizione, quindi aggiornare l'oggetto partizione o dimensione nel server tramite il metodo Update.  
  
 Per rimuovere un oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching>, è necessario innanzitutto rimuoverlo dalla raccolta e successivamente aggiornare l'oggetto padre.  
  
 Una dimensione o una partizione deve essere aggiornata ed elaborata prima che la memorizzazione nella cache attiva sia abilitata e pronta per l'utilizzo.  
  
 Per ulteriori informazioni sui metodi e sulle proprietà disponibili, vedere <xref:Microsoft.AnalysisServices.ProactiveCaching> in <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices>   
 [Introduzione a classi AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Programmazione di oggetti di base OLAP in AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-basic-objects.md)   
 [Oggetti avanzati OLAP in AMO programmazione](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-olap-advanced-objects.md)   
 [Architettura logica &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [Gli oggetti di database &#40; Analysis Services - dati multidimensionali &#41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
