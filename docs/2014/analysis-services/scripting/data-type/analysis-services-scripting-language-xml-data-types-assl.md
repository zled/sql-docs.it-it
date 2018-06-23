---
title: Tipi Analysis Services Scripting Language XML dei dati (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Analysis Services Scripting Language XML Data Types
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ASSL, data types
- Analysis Services Scripting Language, data types
- data types [Analysis Services Scripting Language]
ms.assetid: 8e527916-932e-48ec-9010-f22cd4b721e2
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3420e553b1391fb9645f7e3bffa884e255a90897
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156603"
---
# <a name="analysis-services-scripting-language-xml-data-types-assl"></a>Tipi di dati XML di Analysis Services Scripting Language (ASSL)
  Questa sezione di riferimento contiene informazioni sulla sintassi e l'utilizzo di ogni elemento che funge da tipo nello schema ASSL (Analysis Services Scripting Language).  
  
 Benché lo schema ASSL includa solo elementi XML, dal punto di vista di uno sviluppatore gli elementi descritti in questa sezione corrispondono a tipi, ad esempio `Binding` e `Permission`, utilizzati per definire le proprietà e gli elementi figlio di altri oggetti.  
  
 Gli elementi che fungono da tipo, ad esempio gli elementi oggetto, non sono mai elementi al livello foglia nello schema ASSL, ma dispongono di elementi figlio ed elementi che corrispondono alle proprietà degli oggetti.  
  
 Tuttavia un elemento di tipo viene mai visualizzato come un elemento in uno script che definisce o descrive [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] oggetti. ma costituisce invece il tipo di altri elementi oggetto, in genere definiti dall'attributo `type` dello schema dell'istanza di XML Schema tramite `xsi:type` o `xs:type`. Ad esempio, `<Assembly xsi:type="ClrAssembly">...</Assembly>`.  
  
 In alcuni casi, un tipo deriva da un altro tipo. Il tipo `CubeBinding` deriva ad esempio dal tipo `Binding` padre.  
  
|Elemento|Description|  
|-------------|-----------------|  
|[Tipo di dati Action &#40;ASSL&#41;](action-data-type-assl.md)|Definisce un tipo di dati primitivo astratto che rappresenta un'azione in un [cubo](../objects/cube-element-assl.md) elemento o un [prospettiva](../objects/perspective-element-assl.md) elemento.|  
|[Tipo di dati AggregationAttribute &#40;ASSL&#41;](aggregationattribute-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta l'associazione tra un [aggregazione](../objects/aggregation-element-assl.md) elemento e un attributo.|  
|[Tipo di dati AggregationDesignAttribute &#40;ASSL&#41;](aggregationdesignattribute-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta l'associazione tra un attributo e un [AggregationDesignDimension](dimension-data-type-assl.md) elemento.|  
|[Tipo di dati AggregationDesignDimension &#40;ASSL&#41;](dimension-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta la relazione tra una dimensione del cubo e un [AggregationDesign](../objects/aggregationdesign-element-assl.md) elemento.|  
|[Tipo di dati AggregationDimension &#40;ASSL&#41;](aggregationdimension-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta la relazione tra una dimensione e un [aggregazione](../objects/aggregation-element-assl.md) elemento.|  
|[Tipo di dati AggregationInstanceAttribute &#40;ASSL&#41;](aggregationinstanceattribute-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su un attributo utilizzato da un'istanza di aggregazione.|  
|[Tipo di dati AggregationInstanceCubeDimension &#40;ASSL&#41;](cubedimension-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su una dimensione del cubo utilizzata da un'istanza di aggregazione.|  
|[Tipo di dati AggregationInstanceMeasure &#40;ASSL&#41;](aggregationinstancemeasure-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su una misura utilizzata da un'istanza di aggregazione.|  
|[Tipo di dati assembly &#40;ASSL&#41;](assembly-data-type-assl.md)|Definisce un tipo di dati primitivo astratto che rappresenta un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly o libreria a collegamento dinamico (DLL) un COM associata a un [Server](../objects/server-element-assl.md) oppure [Database](../objects/database-element-assl.md) elemento.|  
|[Tipo di dati AttributeBinding &#40;ASSL&#41;](binding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione per un [attributo](../objects/attribute-element-assl.md) elemento.|  
|[Tipo di dati AttributeTranslation &#40;ASSL&#41;](translation-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta una traduzione associata a un [attributo](../objects/attribute-element-assl.md) elemento|  
|[Tipo di dati binding &#40;ASSL&#41;](binding-data-type-assl.md)|Definisce un tipo di dati primitivo astratto che rappresenta una relazione di dipendenza tra due oggetti in cui i dati o i metadati di un oggetto dipendono dai dati o dai metadati di un oggetto associato.|  
|[Tipo di dati ClrAssembly &#40;ASSL&#41;](clrassembly-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly associato a un [Database](../objects/database-element-assl.md) oppure [Server](../objects/server-element-assl.md) elemento|  
|[Tipo di dati ClrAssemblyFile &#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta uno dei file che compongono un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly ([ClrAssembly](clrassembly-data-type-assl.md) elemento).|  
|[Tipo di dati ColumnBinding &#40;ASSL&#41;](columnbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta l'associazione di una colonna in una vista origine dati a un [DataItem](dataitem-data-type-assl.md) elemento.|  
|[Tipo di dati ComAssembly &#40;ASSL&#41;](comassembly-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta una libreria COM associata a un [Server](../objects/server-element-assl.md) oppure [Database](../objects/database-element-assl.md) elemento.|  
|[Tipo di dati CubeAttribute &#40;ASSL&#41;](cubeattribute-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta un attributo associato a un [cubo](../objects/cube-element-assl.md) elemento.|  
|[Tipo di dati CubeAttributeBinding &#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|Definisce un tipo di dati derivato che rappresenta l'associazione di un attributo in una dimensione del cubo a un'azione o una colonna della struttura di data mining.|  
|[Cubebinding-tipo di dati &#40;out-of-line&#41; &#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|Definisce un tipo di dati primitivo che rappresenta la relazione tra un [cubo](../objects/cube-element-assl.md) elemento e una [DataSource](../objects/datasource-element-assl.md) elemento.|  
|[Tipo di dati CubeDimension &#40;ASSL&#41;](cubedimension-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta la relazione tra una dimensione e un cubo.|  
|[Tipo di dati CubeDimensionBinding &#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta l'associazione di un [dimensione](../objects/dimension-element-assl.md), [misura](../objects/measure-element-assl.md), o [MiningModel](../objects/miningmodel-element-assl.md) elemento da una dimensione del cubo.|  
|[Tipo di dati CubeDimensionPermission &#40;ASSL&#41;](permission-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le autorizzazioni per un singolo ruolo in una dimensione specifica di un cubo.|  
|[Tipo di dati CubeHierarchy &#40;ASSL&#41;](hierarchy-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su un [gerarchia](../objects/hierarchy-element-assl.md) elemento in un [cubo](../objects/cube-element-assl.md) elemento.|  
|[Tipo di dati DataBlock &#40;ASSL&#41;](datablock-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta una raccolta di blocchi di dati utilizzato per archiviare il contenuto binario di un [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) elemento.|  
|[Tipo di dati DataItem &#40;ASSL&#41;](dataitem-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le caratteristiche relative ai dati di un elemento di dati, ad esempio una colonna o un attributo.|  
|[Tipo di dati DataMiningMeasureGroupDimension &#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta la relazione tra un gruppo di misure e una dimensione di data mining.|  
|[Tipo di dati di origine dati &#40;ASSL&#41;](datasource-data-type-assl.md)|Definisce un tipo di dati primitivo astratto che rappresenta un'origine dati in un [Database](../objects/database-element-assl.md) elemento.|  
|[Tipo di dati DataSourceViewBinding &#40;ASSL&#41;](datasourceviewbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione tra una vista origine dati e un elemento padre.|  
|[Tipo di dati DegenerateMeasureGroupDimension &#40;ASSL&#41;](degeneratemeasuregroupdimension-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta la relazione tra una dimensione degenerata, ovvero una dimensione dei fatti, e un gruppo di misure.|  
|[Tipo di dati di dimensione &#40;ASSL&#41;](dimension-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta una dimensione del database.|  
|[Tipo di dati DimensionAttribute &#40;ASSL&#41;](dimensionattribute-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta un attributo in una dimensione.|  
|[Tipo di dati DimensionBinding &#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta l'associazione tra un'origine dati e un [dimensione](../objects/dimension-element-assl.md) elemento.|  
|[Tipo di dati DimensionPermission &#40;ASSL&#41;](permission-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta le autorizzazioni assegnate a una dimensione del database.|  
|[Tipo di dati DrillThroughAction &#40;ASSL&#41;](drillthroughaction-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'azione drill-through.|  
|[Tipo di dati DSVTableBinding &#40;ASSL&#41;](tablebinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta l'associazione tra una tabella e un [DataSourceView](../objects/datasourceview-element-assl.md) elemento.|  
|[Tipo di dati EventColumn &#40;ASSL&#41;](eventcolumn-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta una colonna di informazioni da acquisire per un [evento](../objects/event-element-assl.md) come parte dell'elemento un [traccia](../objects/trace-element-assl.md) elemento.|  
|[Tipo di dati Hierarchy &#40;ASSL&#41;](hierarchy-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta una gerarchia in una dimensione.|  
|[Tipo di dati ImpersonationInfo &#40;ASSL&#41;](impersonationinfo-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni utilizzate per rappresentare un utente.|  
|[Tipo di dati IncrementalProcessingNotification &#40;ASSL&#41;](incrementalprocessingnotification-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta le informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento relative a una query da eseguire per determinare lo stato di avanzamento dell'elaborazione incrementale.|  
|[Tipo di dati InheritedBinding &#40;ASSL&#41;](inheritedbinding-data-type-assl.md)|Definisce un tipo di dati derivato che indica che un [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md) elemento eredita le associazioni dall'attributo.|  
|[Tipo di dati ManyToManyMeasureGroupDimension &#40;ASSL&#41;](manytomanymeasuregroupdimension-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta la relazione tra una dimensione molti-a-molti e un gruppo di misure.|  
|[Tipo di dati MeasureBinding &#40;ASSL&#41;](measurebinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta l'associazione di una misura all'elemento padre.|  
|[Tipo di dati MeasureGroupAttribute &#40;ASSL&#41;](measuregroupattribute-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta la relazione tra un attributo e un gruppo di misure.|  
|[Tipo di dati MeasureGroupBinding &#40;ASSL&#41;](measuregroupbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione a un [MeasureGroup](../objects/group-element-assl.md) elemento.|  
|[Tipo di dati MeasureGroupBinding &#40;out-of-line&#41; &#40;ASSL&#41;](measuregroupbinding-data-type-out-of-line-assl.md)|Definisce un tipo di dati primitivo che rappresenta un'associazione a un gruppo di misure.|  
|[Tipo di dati MeasureGroupDimension &#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|Definisce un tipo di dati primitivo astratto che rappresenta la relazione tra una dimensione e un gruppo di misure.|  
|[Tipo di dati MeasureGroupDimensionBinding &#40;ASSL&#41;](measuregroupdimensionbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione tra una dimensione e un gruppo di misure.|  
|[Tipo di dati MeasureGroupHierarchy &#40;ASSL&#41;](measuregrouphierarchy-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su una gerarchia in un gruppo di misure.|  
|[Tipo di dati MiningModelColumn &#40;ASSL&#41;](miningmodelcolumn-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su una colonna in una [MiningModel](../objects/miningmodel-element-assl.md) elemento.|  
|[Tipo di dati MiningModelingFlag &#40;ASSL&#41;](miningmodelingflag-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta i flag di modellazione disponibili per un [ModelingFlag](../objects/modelingflag-element-assl.md) elemento.|  
|[Tipo di dati MiningStructureColumn &#40;ASSL&#41;](miningstructurecolumn-data-type-assl.md)|Definisce un tipo di dati primitivo astratto che rappresenta le informazioni su una colonna in una [MiningStructure](../objects/miningstructure-element-assl.md) elemento.|  
|[Tipo di dati OlapDataSource &#40;ASSL&#41;](olapdatasource-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un oggetto multidimensionale [DataSource](../objects/datasource-element-assl.md) elemento.|  
|[Tipo di dati PartitionBinding &#40;ASSL&#41;](partitionbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione a un [partizione](../objects/partition-element-assl.md) elemento.|  
|[Tipo di dati di autorizzazione &#40;ASSL&#41;](permission-data-type-assl.md)|Definisce un tipo di dati primitivo astratto che rappresenta le informazioni su una singola autorizzazione.|  
|[Tipo di dati PerspectiveAction &#40;ASSL&#41;](perspectiveaction-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su un'azione in un [prospettiva](../objects/perspective-element-assl.md) elemento.|  
|[Tipo di dati PerspectiveAttribute &#40;ASSL&#41;](perspectiveattribute-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su un attributo in un [PerspectiveDimension](perspectivedimension-data-type-assl.md) elemento.|  
|[Tipo di dati PerspectiveCalculation &#40;ASSL&#41;](perspectivecalculation-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta la relazione tra un calcolo e un [prospettiva](../objects/perspective-element-assl.md) elemento.|  
|[Tipo di dati PerspectiveDimension &#40;ASSL&#41;](perspectivedimension-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su una dimensione in una prospettiva.|  
|[Tipo di dati PerspectiveHierarchy &#40;ASSL&#41;](perspectivehierarchy-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su una gerarchia in una [PerspectiveDimension](perspectivedimension-data-type-assl.md) elemento.|  
|[Tipo di dati PerspectiveKpi &#40;ASSL&#41;](perspectivekpi-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su un indicatore di prestazioni chiave (KPI) in un [prospettiva](../objects/perspective-element-assl.md) elemento.|  
|[Tipo di dati PerspectiveMeasure &#40;ASSL&#41;](perspectivemeasure-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su una misura in un [PerspectiveMeasureGroup](perspectivemeasuregroup-data-type-assl.md) elemento.|  
|[Tipo di dati PerspectiveMeasureGroup &#40;ASSL&#41;](perspectivemeasuregroup-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta le informazioni su un gruppo di misure in un [prospettiva](../objects/perspective-element-assl.md) elemento.|  
|[Tipo di dati ProactiveCachingBinding &#40;ASSL&#41;](proactivecachingbinding-data-type-assl.md)|Definisce un tipo di dati derivato astratto che rappresenta le informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento relative alle modifiche dell'origine dati che richiedono la ricompilazione della cache o sullo stato del processo di ricompilazione.|  
|[Tipo di dati ProactiveCachingIncrementalProcessingBinding &#40;ASSL&#41;](proactivecachingincrementalprocessingbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento sullo stato del processo di ricompilazione della cache.|  
|[Tipo di dati ProactiveCachingInheritedBinding &#40;ASSL&#41;](proactivecachinginheritedbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta le informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento relative alle modifiche dell'origine dati in tabelle e nelle viste identificate tramite le associazioni dati esistenti che richiedono la ricompilazione della cache.|  
|[Tipo di dati ProactiveCachingObjectNotificationBinding &#40;ASSL&#41;](proactivecachingobjectnotificationbinding-data-type-assl.md)|Definisce un tipo di dati derivato astratto che rappresenta le informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento relative alle modifiche di origine dati, tabelle e viste specificate o in tabelle e nelle viste identificate tramite le associazioni dati esistenti che richiedono la ricompilazione della cache.|  
|[Tipo di dati ProactiveCachingQueryBinding &#40;ASSL&#41;](querybinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta le informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento relative alle modifiche dell'origine dati in tabelle e nelle viste identificate tramite l'esecuzione delle query specificate che richiedono la ricompilazione della cache.|  
|[Tipo di dati ProactiveCachingTablesBinding &#40;ASSL&#41;](proactivecachingtablesbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta le informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento relative alle modifiche dell'origine dati in tabelle e viste che richiedono la ricompilazione della cache specificate.|  
|[Tipo di dati PushedDataSource &#40;ASSL&#41;](pusheddatasource-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta un'origine dati (ad esempio un [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] pacchetto) utilizzato per il "push" dati in un [cubo](../objects/cube-element-assl.md) elemento.|  
|[Tipo di dati QueryBinding &#40;ASSL&#41;](querybinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta l'associazione di un [DataSource](../objects/datasource-element-assl.md) elemento con un [QueryDefinition](../properties/querydefinition-element-assl.md) elemento.|  
|[Tipo di dati ReferenceMeasureGroupDimension &#40;ASSL&#41;](referencemeasuregroupdimension-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta una dimensione indirettamente correlata alla tabella dei fatti tramite una dimensione intermedia. Un gruppo di misure Sales può, ad esempio, fare riferimento a una dimensione Geography, correlata tramite la dimensione Customer.|  
|[Tipo di dati RegularMeasureGroupDimension &#40;ASSL&#41;](regularmeasuregroupdimension-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta la relazione di tipo Regolare tra una dimensione e un gruppo di misure.|  
|[Tipo di dati RelationalDataSource &#40;ASSL&#41;](relationaldatasource-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un [DataSource](../objects/datasource-element-assl.md) elemento basato su un'origine dati relazionale.|  
|[Tipo di dati ReportAction &#40;ASSL&#41;](reportaction-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'azione che genera un report di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Tipo di dati RowBinding &#40;ASSL&#41;](rowbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione alle righe di una tabella in un [DataSourceView](../objects/datasourceview-element-assl.md) elemento.|  
|[Tipo di dati ScalarMiningStructureColumn &#40;ASSL&#41;](scalarminingstructurecolumn-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) elemento che contiene valori scalari, a differenza delle tabelle nidificate associate le [TableMiningStructureColumn](tableminingstructurecolumn-data-type-assl.md) elemento che contiene tabelle nidificate.|  
|[Tipo di dati StandardAction &#40;ASSL&#41;](standardaction-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta qualsiasi [azione](../objects/action-element-assl.md) elemento diverso da un [DrillThroughAction](drillthroughaction-data-type-assl.md) elemento o un [ReportAction](reportaction-data-type-assl.md) elemento.|  
|[Tipo di dati TableBinding &#40;ASSL&#41;](tablebinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione a una tabella.|  
|[Tipo di dati TableMiningStructureColumn &#40;ASSL&#41;](tableminingstructurecolumn-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) elemento che contiene tabelle nidificate, a differenza dei valori scalari associati con il [ScalarMiningStructureColumn](scalarminingstructurecolumn-data-type-assl.md) elemento che contiene valori scalari.|  
|[Tipo di dati TabularBinding &#40;ASSL&#41;](tabularbinding-data-type-assl.md)|Definisce un tipo di dati derivato astratto che rappresenta un'associazione a un elemento tabulare, ad esempio una dimensione di un cubo o una tabella.|  
|[Tipo di dati TimeAttributeBinding &#40;ASSL&#41;](timebinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione "segnaposto" per gli elementi di dati generati in una dimensione temporale del server, ad esempio le colonne chiave di un attributo.|  
|[Tipo di dati TimeBinding &#40;ASSL&#41;](timebinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un'associazione a periodi di tempo.|  
|[Tipo di dati Translation &#40;ASSL&#41;](translation-data-type-assl.md)|Definisce un tipo di dati primitivo che rappresenta una versione localizzata.|  
|[Tipo di dati UserDefinedGroupBinding &#40;ASSL&#41;](userdefinedgroupbinding-data-type-assl.md)|Definisce un tipo di dati derivato che rappresenta un raggruppamento definito dall'utente per un attributo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia Analysis Services Scripting Language XML elemento &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  