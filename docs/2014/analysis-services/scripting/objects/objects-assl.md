---
title: Oggetti (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ASSL, objects
- objects [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
ms.assetid: 0f672b93-c317-47e5-b44d-ecea9b587c98
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 246126f6ec82a104b05687c088c0bf3d2a614da6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066602"
---
# <a name="objects-assl"></a>Oggetti (ASSL)
  Questa sezione di riferimento contiene informazioni sulla sintassi e l'utilizzo di ogni elemento che funge da oggetto nello schema ASSL (Analysis Services Scripting Language).  
  
 Benché lo schema ASSL includa solo elementi XML, dal punto di vista dello sviluppatore, gli elementi descritti in questa sezione corrispondono a oggetti, ad esempio `Database`, `Cube`, e `Dimension` oggetti nella gerarchia di oggetti contenuti in un istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 Gli oggetti non sono mai elementi al livello foglia nello schema ASSL, ma dispongono di elementi figlio ed elementi che corrispondono alle proprietà degli oggetti.  
  
 In alcuni casi, un elemento a livello foglia nello schema che può sembrare una proprietà viene classificato come oggetto perché il tipo dell'elemento è un tipo oggetto. Ad esempio, `Source` di un oggetto `Dimension` è di tipo `DimensionBinding`.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Elemento|Description|  
|-------------|-----------------|  
|[Elemento dell'account &#40;ASSL&#41;](account-element-assl.md)|Contiene informazioni dettagliate su un tipo di conto all'interno di un [Database](database-element-assl.md) elemento.|  
|[Elemento Action &#40;ASSL&#41;](action-element-assl.md)|Contiene informazioni su un'azione disponibile in un [cubo](cube-element-assl.md) elemento o un [prospettiva](perspective-element-assl.md) elemento.|  
|[Elemento aggregation &#40;ASSL&#41;](aggregation-element-assl.md)|Definisce una singola aggregazione per un [partizione](partition-element-assl.md) elemento.|  
|[Elemento AggregationDesign &#40;ASSL&#41;](aggregationdesign-element-assl.md)|Definisce un set di definizioni di aggregazione che possono essere condivise tra più partizioni in un database.|  
|[Elemento AggregationInstance &#40;ASSL&#41;](aggregationinstance-element-assl.md)|Definisce un'istanza di aggregazione per una partizione.|  
|[Elemento AlgorithmParameter &#40;ASSL&#41;](algorithmparameter-element-assl.md)|Definisce un parametro per l'algoritmo utilizzato da un [MiningModel](miningmodel-element-assl.md) elemento.|  
|[Elemento AllMemberTranslation &#40;ASSL&#41;](translation-element-assl.md)|Contiene una traduzione per la didascalia del membro totale di un [gerarchia](hierarchy-element-assl.md) elemento.|  
|[Elemento di annotazione &#40;ASSL&#41;](annotation-element-assl.md)|Contiene elementi utilizzati per estendere lo schema ASSL.|  
|[Elemento assembly &#40;ASSL&#41;](assembly-element-assl.md)|Rappresenta un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly o libreria a collegamento dinamico (DLL) un COM associata a un [Server](server-element-assl.md) elemento o un [Database](database-element-assl.md) elemento.|  
|[Elemento dell'attributo &#40;ASSL&#41;](attribute-element-assl.md)|Contiene la descrizione di un attributo.|  
|[Elemento AttributeAllMemberTranslation &#40;ASSL&#41;](attributeallmembertranslation-element-assl.md)|Contiene una traduzione per la didascalia del membro totale di un [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) elemento.|  
|[Elemento Attributepermissions &#40;ASSL&#41;](attributepermission-element-assl.md)|Definisce le autorizzazioni che i membri di un [ruolo](role-element-assl.md) elemento avere gli attributi di una singola dimensione in un [cubo](cube-element-assl.md) elemento.|  
|[Elemento AttributeRelationship &#40;ASSL&#41;](attributerelationship-element-assl.md)|Fornisce informazioni dettagliate sulla relazione tra due attributi.|  
|[Bloccare l'elemento &#40;ASSL&#41;](block-element-assl.md)|Contiene tutte o una parte del contenuto binario di un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) elemento.|  
|[Elemento Calculation &#40;ASSL&#41;](calculation-element-assl.md)|Associa un calcolo con a una [prospettiva](perspective-element-assl.md) elemento.|  
|[Elemento CalculationProperty &#40;ASSL&#41;](calculationproperty-element-assl.md)|Contiene una raccolta di proprietà dell'interfaccia utente per un calcolo utilizzato un' [MdxScript](mdxscript-element-assl.md) elemento.|  
|[Elemento CaptionColumn &#40;ASSL&#41;](column-element-assl.md)|Definisce la colonna che fornisce la didascalia per l'attributo.|  
|[Elemento CellPermission &#40;ASSL&#41;](cellpermission-element-assl.md)|Vengono descritte le autorizzazioni che i membri di un [ruolo](role-element-assl.md) elemento avere le singole celle all'interno di un [cubo](cube-element-assl.md) elemento.|  
|[Elemento Column &#40;ASSL&#41;](column-element-assl.md)|Descrive una colonna nella raccolta di colonne associate all'elemento padre.|  
|[Elemento di comando &#40;ASSL&#41;](command-element-assl.md)|Definisce un comando disponibile per l'utilizzo nel contesto dell'elemento padre della raccolta Commands.|  
|[Elemento del cubo &#40;ASSL&#41;](cube-element-assl.md)|Definisce un cubo regolare, virtuale o collegato in un' [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [Database](database-element-assl.md) elemento.|  
|[Elemento CubePermission &#40;ASSL&#41;](cubepermission-element-assl.md)|Definisce le autorizzazioni dei membri di un determinato [ruolo](role-element-assl.md) elemento in uno specifico [cubo](cube-element-assl.md) elemento.|  
|[Elemento CustomRollupColumn &#40;ASSL&#41;](customrollupcolumn-element-assl.md)|Definisce i dettagli della colonna che forniscono una formula personalizzata di rollup.|  
|[Elemento CustomRollupPropertiesColumn &#40;ASSL&#41;](customrolluppropertiescolumn-element-assl.md)|Definisce i dettagli di una colonna che forniscono le proprietà di una formula personalizzata di rollup.|  
|[Elemento di dati &#40;ASSL&#41;](data-element-assl.md)|Contiene (nella raccolta dell'elemento figlio `Block` elementi) del contenuto binario di un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) elemento.|  
|[Elemento database &#40;ASSL&#41;](database-element-assl.md)|Definisce un database di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento DatabasePermission &#40;ASSL&#41;](databasepermission-element-assl.md)|Definisce le autorizzazioni predefinite in un [Database](database-element-assl.md) elemento per uno specifico [ruolo](role-element-assl.md) elemento.|  
|[Elemento DataSource &#40;ASSL&#41;](datasource-element-assl.md)|Definisce un'origine dati in un [Database](database-element-assl.md) elemento.|  
|[Elemento DataSourcePermission &#40;ASSL&#41;](datasourcepermission-element-assl.md)|Definisce le autorizzazioni predefinite in un [DataSource](../data-type/datasource-data-type-assl.md) tipo di dati per uno specifico [ruolo](role-element-assl.md) elemento.|  
|[Elemento DataSourceView &#40;ASSL&#41;](datasourceview-element-assl.md)|Definisce una vista origine dati utilizzata da un [Database](database-element-assl.md) elemento.|  
|[Elemento della dimensione &#40;ASSL&#41;](dimension-element-assl.md)|Definisce una dimensione.|  
|[Elemento DimensionPermission &#40;ASSL&#41;](dimensionpermission-element-assl.md)|Definisce le autorizzazioni che appartengono a un determinato [ruolo](role-element-assl.md) elemento per una dimensione di database specifico o una dimensione del cubo.|  
|[Elemento ErrorConfiguration &#40;ASSL&#41;](errorconfiguration-element-assl.md)|Specifica le impostazioni per la gestione di errori che possono verificarsi durante l'elaborazione dell'elemento padre.|  
|[Elemento di un evento &#40;ASSL&#41;](event-element-assl.md)|Definisce un evento da acquisire come parte di un [traccia](trace-element-assl.md) elemento.|  
|[File di elemento &#40;ASSL&#41;](file-element-assl.md)|Definisce uno dei file che compongono un [ClrAssembly](../data-type/assembly-data-type-assl.md) elemento.|  
|[Elemento ForeignKeyColumn &#40;ASSL&#41;](keycolumn-element-assl.md)|Identifica il join a una tabella padre per un'origine dati relazionale.|  
|[Elemento Group &#40;ASSL&#41;](group-element-assl.md)|Definisce un gruppo di membri associati a un attributo.|  
|[Elemento Hierarchy &#40;ASSL&#41;](hierarchy-element-assl.md)|Definisce una gerarchia in una dimensione.|  
|[Elemento IncrementalProcessingNotification &#40;ASSL&#41;](incrementalprocessingnotification-element-assl.md)|Contiene informazioni per il [ProactiveCaching](proactivecaching-element-assl.md) elemento relative a una query da eseguire per determinare lo stato di avanzamento dell'elaborazione incrementale.|  
|[Elemento KeyColumn &#40;ASSL&#41;](keycolumn-element-assl.md)|Contiene la definizione di una colonna che corrisponde alla, o fa parte della, chiave per un attributo.|  
|[Elemento KPI &#40;ASSL&#41;](kpi-element-assl.md)|Definisce un indicatore di prestazioni chiave (KPI) all'interno di un [cubo](cube-element-assl.md) elemento o un [prospettiva](perspective-element-assl.md) elemento.|  
|[Livello di elemento &#40;ASSL&#41;](level-element-assl.md)|Definisce un livello in un [gerarchia](hierarchy-element-assl.md) elemento.|  
|[Elemento MdxScript &#40;ASSL&#41;](mdxscript-element-assl.md)|Contiene informazioni su uno script MDX (Multidimensional Expressions) che è associato un [cubo](cube-element-assl.md) elemento.|  
|[Elemento di misure &#40;ASSL&#41;](measure-element-assl.md)|Definisce una misura.|  
|[Elemento MeasureGroup &#40;ASSL&#41;](measuregroup-element-assl.md)|Definisce un set di misure allo stesso livello di granularità.|  
|[Elemento membro &#40;ASSL&#41;](member-element-assl.md)|Contiene il nome di un membro di un [gruppo](group-element-assl.md) elemento o di un [ruolo](role-element-assl.md) elemento.|  
|[Elemento MiningModel &#40;ASSL&#41;](miningmodel-element-assl.md)|Definisce un singolo modello di data mining.|  
|[Elemento MiningModelPermission &#40;ASSL&#41;](miningmodelpermission-element-assl.md)|Definisce i membri di autorizzazioni di un [ruolo](role-element-assl.md) elemento dispone di un singolo [MiningModel](miningmodel-element-assl.md) elemento.|  
|[Elemento MiningStructure &#40;ASSL&#41;](miningstructure-element-assl.md)|Definisce la struttura per un set di modelli di data mining.|  
|[Elemento MiningStructurePermission &#40;ASSL&#41;](miningstructurepermission-element-assl.md)|Definisce le autorizzazioni che i membri di un [ruolo](role-element-assl.md) elemento dispone di un singolo [MiningStructure](miningstructure-element-assl.md) elemento.|  
|[Elemento ModelingFlag &#40;ASSL&#41;](modelingflag-element-assl.md)|Contiene un flag di modellazione per una colonna in una struttura di data mining o un modello di data mining.|  
|[Elemento NameColumn &#40;ASSL&#41;](namecolumn-element-assl.md)|Identifica la colonna che fornisce il nome dell'elemento padre.|  
|[Elemento NamingTemplateTranslation &#40;ASSL&#41;](namingtemplatetranslation-element-assl.md)|Fornisce una versione localizzata del `NamingTemplate` elemento per un elemento padre [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md) tipo di dati.|  
|[Elemento di partizione &#40;ASSL&#41;](partition-element-assl.md)|Definisce una partizione di un [MeasureGroup](measuregroup-element-assl.md) elemento o un'associazione della partizione in un out-of-line [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)elemento.|  
|[Elemento Perspective &#40;ASSL&#41;](perspective-element-assl.md)|Definisce i dettagli per una prospettiva di un [cubo](cube-element-assl.md) elemento.|  
|[Elemento ProactiveCaching &#40;ASSL&#41;](proactivecaching-element-assl.md)|Definisce impostazioni di memorizzazione attiva nella cache per l'elemento padre.|  
|[Elemento QueryNotification &#40;ASSL&#41;](querynotification-element-assl.md)|Contiene informazioni per il [ProactiveCaching](proactivecaching-element-assl.md) elemento relative a una query da eseguire per determinare se un'origine dati è stata modificata.|  
|[Elemento ReportFormatParameter &#40;ASSL&#41;](reportformatparameter-element-asl.md)|Contiene il nome e il valore di un parametro che specifica come un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] report formattato in fase di esecuzione.|  
|[Elemento ReportParameter &#40;ASSL&#41;](reportparameter-element-assl.md)|Contiene il nome e il valore di un parametro passato a un report di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] in fase di esecuzione.|  
|[Elemento Role &#40;ASSL&#41;](role-element-assl.md)|Contiene informazioni su un ruolo di sicurezza.|  
|[Elemento server &#40;ASSL&#41;](server-element-assl.md)|Descrive un'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|[Elemento ServerProperty &#40;ASSL&#41;](serverproperty-element-assl.md)|Definisce una proprietà del server associata a un [Server](server-element-assl.md) elemento.|  
|[Elemento SkippedLevelsColumn &#40;ASSL&#41;](skippedlevelscolumn-element-assl.md)|Fornisce i dettagli di una colonna che archivia il numero di livelli ignorati (vuoti) tra ogni membro e il relativo elemento padre.|  
|[Elemento SourceMeasureGroup &#40;ASSL&#41;](sourcemeasuregroup-element-assl.md)|Identifica il gruppo di misure che funge da origine dati per una colonna della struttura di data mining.|  
|[Elemento TableNotification &#40;ASSL&#41;](tablenotification-element-assl.md)|Contiene informazioni per il [ProactiveCaching](proactivecaching-element-assl.md) elemento su una tabella o vista in un'origine dati che è stata modificata.|  
|[Elemento Trace &#40;ASSL&#41;](trace-element-assl.md)|Definisce una traccia su cui è possibile eseguire query.|  
|[Elemento Translation &#40;ASSL&#41;](translation-element-assl.md)|Fornisce una traduzione localizzata per l'elemento padre del [traduzioni](../collections/translations-element-assl.md) insieme.|  
|[Elemento UnaryOperatorColumn &#40;ASSL&#41;](unaryoperatorcolumn-element-assl.md)|Definisce i dettagli di una colonna che fornisce un operatore unario.|  
|[Elemento UnknownMemberTranslation &#40;ASSL&#41;](unknownmembertranslation-element-assl.md)|Contiene una traduzione per la didascalia del [UnknownMember](../properties/unknownmember-element-assl.md) elemento per un [dimensione](dimension-element-assl.md) elemento.|  
|[Elemento ValueColumn &#40;ASSL&#41;](valuecolumn-element-assl.md)|Identifica la colonna che fornisce il valore dell'elemento padre.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia Analysis Services Scripting Language XML elemento &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  