---
title: Raccolte (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- collections [Analysis Services Scripting Language]
- Analysis Services Scripting Language, collections
- ASSL, collections
ms.assetid: 072b8c6b-1550-4cab-ae64-ba0e3e60b059
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f549a8d84f356b9315cdf3ec03ee41234e4dd0d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199711"
---
# <a name="collections-assl"></a>Raccolte (ASSL)
  Questa sezione di riferimento contiene informazioni sulla sintassi e l'utilizzo di ogni elemento che funge da raccolta nello schema ASSL (Analysis Services Scripting Language).  
  
 Benché lo schema ASSL includa solo elementi XML, dal punto di vista di uno sviluppatore gli elementi descritti in questa sezione corrispondono a raccolte di oggetti, ad esempio le raccolte `Dimensions` e `Cubes`.  
  
 Le raccolte sono per lo più set di elementi oggetto, in cui un sostantivo plurale definisce la raccolta, ad esempio `Cubes`, che contiene a sua volta elementi designati dallo stesso sostantivo in forma singolare, ad esempio `Cube`.  
  
 In alcuni casi lo schema non segue questa regola generale. La raccolta `ClassifiedColumns`, ad esempio, contiene elementi `ClassifiedColumnID`.  
  
 In altri casi, una raccolta contiene elementi che corrispondono a proprietà di oggetti e non a oggetti. La raccolta `Aliases`, ad esempio, contiene proprietà `Alias`, ognuna delle quali è un valore stringa semplice.  
  
|Elemento|Description|  
|-------------|-----------------|  
|[Account di elemento &#40;ASSL&#41;](accounts-element-assl.md)|Contiene la raccolta di tipi di conto definiti in un [Database](../objects/database-element-assl.md) elemento.|  
|[Elemento Actions &#40;ASSL&#41;](actions-element-assl.md)|Contiene la raccolta di azioni per un [cubo](../objects/cube-element-assl.md) oppure [prospettiva](../objects/perspective-element-assl.md) elemento.|  
|[Elemento AggregationDesigns &#40;ASSL&#41;](aggregationdesigns-element-assl.md)|Contiene la raccolta di progettazioni di aggregazioni che possono essere condivise tra più partizioni in un database.|  
|[Elemento AggregationInstances &#40;ASSL&#41;](aggregationinstances-element-assl.md)|Contiene la raccolta di istanze di aggregazione definite in un [partizione](../objects/partition-element-assl.md) elemento.|  
|[Elemento Aggregations &#40;ASSL&#41;](aggregations-element-assl.md)|Contiene la raccolta di aggregazioni definite per un [AggregationDesign](../objects/aggregationdesign-element-assl.md) elemento.|  
|[Elemento AlgorithmParameters &#40;ASSL&#41;](algorithmparameters-element-assl.md)|Contiene la raccolta di parametri per l'algoritmo utilizzato da un [MiningModel](../objects/miningmodel-element-assl.md) elemento.|  
|[Elemento alias &#40;ASSL&#41;](aliases-element-assl.md)|Contiene la raccolta di [Alias](../properties/alias-element-assl.md) gli elementi associati a un [Account](../objects/account-element-assl.md) elemento|  
|[Elemento AllMemberTranslations &#40;ASSL&#41;](translations-element-assl.md)|Contiene la raccolta di [Translation](../objects/translation-element-assl.md) gli elementi per la didascalia del membro totale di un [gerarchia](../objects/hierarchy-element-assl.md) elemento.|  
|[Elemento Annotations &#40;ASSL&#41;](annotations-element-assl.md)|Contiene la raccolta di [annotazione](../objects/annotation-element-assl.md) elementi associati all'elemento padre.|  
|[Elemento Assemblies &#40;ASSL&#41;](assemblies-element-assl.md)|Contiene la raccolta di [assieme](../objects/assembly-element-assl.md) gli elementi associati a un [Server](../objects/server-element-assl.md) elemento o un [Database](../objects/database-element-assl.md) elemento.|  
|[Elemento AttributeAllMemberTranslations &#40;ASSL&#41;](attributeallmembertranslations-element-assl.md)|Contiene la raccolta di traduzioni per la didascalia del membro Totale della dimensione.|  
|[Elemento AttributePermissions &#40;ASSL&#41;](attributepermissions-element-assl.md)|Contiene la raccolta di autorizzazioni per gli attributi per un singolo [ruolo](../objects/role-element-assl.md) elemento in una dimensione specifica di un [cubo](../objects/cube-element-assl.md) elemento.|  
|[Elemento AttributeRelationships &#40;ASSL&#41;](relationships-element-assl.md)|Contiene la raccolta di [AttributeRelationship](../objects/attributerelationship-element-assl.md) elementi per l'attributo.|  
|[Elemento Attributes &#40;ASSL&#41;](attributes-element-assl.md)|Contiene la raccolta di attributi per la dimensione associata.|  
|[Blocca l'elemento &#40;ASSL&#41;](blocks-element-assl.md)|Contiene la raccolta di blocchi di dati binari che rappresentano contenuto binario di un [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) elemento.|  
|[Elemento Calculationproperty &#40;ASSL&#41;](calculationproperties-element-assl.md)|Contiene la raccolta di [CalculationProperty](../objects/calculationproperty-element-assl.md) gli elementi associati a un [MdxScript](../objects/mdxscript-element-assl.md) elemento.|  
|[Elemento Calculations &#40;ASSL&#41;](calculations-element-assl.md)|Contiene la raccolta di [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md) gli elementi associati a un [prospettiva](../objects/perspective-element-assl.md) elemento.|  
|[Elemento CellPermissions &#40;ASSL&#41;](cellpermissions-element-assl.md)|Contiene la raccolta di autorizzazioni per le celle nell'oggetto associato [cubo](../objects/cube-element-assl.md) elemento.|  
|[Elemento ClassifiedColumns &#40;ASSL&#41;](columns-element-assl.md)|Contiene la raccolta di colonne correlate classificate dal [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) elemento.|  
|[Elemento Columns &#40;ASSL&#41;](columns-element-assl.md)|Contiene la raccolta di colonne associate all'elemento padre.|  
|[I comandi di elemento &#40;ASSL&#41;](commands-element-assl.md)|Contiene la raccolta di elementi [Command](../objects/command-element-assl.md) associati a un elemento [MdxScript](../objects/mdxscript-element-assl.md).|  
|[Elemento CubePermissions &#40;ASSL&#41;](cubepermissions-element-assl.md)|Contiene la raccolta di autorizzazioni applicabili a un [cubo](../objects/cube-element-assl.md) elemento.|  
|[Cubi di elemento &#40;ASSL&#41;](cubes-element-assl.md)|Contiene la raccolta di [cubo](../objects/cube-element-assl.md) gli elementi associati a un [Database](../objects/database-element-assl.md) elemento.|  
|[Elemento DatabasePermissions &#40;ASSL&#41;](databasepermissions-element-assl.md)|Contiene la raccolta di [DatabasePermission](../objects/databasepermission-element-assl.md) gli elementi associati a un [Database](../objects/database-element-assl.md) elemento.|  
|[Elemento Databases &#40;ASSL&#41;](databases-element-assl.md)|Contiene la raccolta di [Database](../objects/database-element-assl.md) gli elementi associati a un [Server](../objects/server-element-assl.md) elemento.|  
|[Elemento DataSources &#40;ASSL&#41;](datasources-element-assl.md)|Contiene la raccolta di [DataSourcePermission](../objects/datasourcepermission-element-assl.md) gli elementi associati a un [DataSource](../data-type/datasource-data-type-assl.md) tipo di dati.|  
|[Elemento DataSourcePermissions &#40;ASSL&#41;](datasourcepermissions-element-assl.md)|Contiene la raccolta di [DataSource](../objects/datasource-element-assl.md) gli elementi associati a un [Database](../objects/database-element-assl.md) elemento.|  
|[Elemento DataSourceViews &#40;ASSL&#41;](datasourceviews-element-assl.md)|Contiene la raccolta di [DataSourceView](../objects/datasourceview-element-assl.md) gli elementi associati a un [Database](../objects/database-element-assl.md) elemento.|  
|[Elemento DimensionPermissions &#40;ASSL&#41;](dimensionpermissions-element-assl.md)|Contiene la raccolta di autorizzazioni applicabili a un [dimensione](../objects/dimension-element-assl.md) elemento o una [CubePermission](../objects/cubepermission-element-assl.md) elemento.|  
|[Dimensioni elemento di tipo &#40;ASSL&#41;](dimensions-element-assl.md)|Contiene la raccolta di dimensioni associate all'elemento padre.|  
|[Elemento Events &#40;ASSL&#41;](events-element-assl.md)|Definisce la raccolta di elementi Event da acquisire tramite un [traccia](../objects/trace-element-assl.md).|  
|[File di elemento &#40;ASSL&#41;](files-element-assl.md)|Contiene la raccolta di [File](../objects/file-element-assl.md) gli elementi che costituiscono un [ClrAssembly](../data-type/assembly-data-type-assl.md) elemento.|  
|[Elemento ForeignKeyColumns &#40;ASSL&#41;](keycolumns-element-assl.md)|Contiene la raccolta di colonne che identificano il join alla tabella padre per un'origine dati relazionale.|  
|[Gruppi elemento &#40;ASSL&#41;](groups-element-assl.md)|Contiene la raccolta di gruppi di membri associati a un attributo.|  
|[Elemento hierarchies &#40;ASSL&#41;](hierarchies-element-assl.md)|Contiene la raccolta di [gerarchia](../objects/hierarchy-element-assl.md) elementi associati all'elemento padre.|  
|[Elemento IncrementalProcessingNotifications &#40;ASSL&#41;](incrementalprocessingnotifications-element-assl.md)|Contiene la raccolta di [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md) gli elementi che forniscono informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) sulle query da eseguire per determinare lo stato dell'elemento elaborazione incrementale.|  
|[Elemento KeyColumns &#40;ASSL&#41;](keycolumns-element-assl.md)|Contiene la raccolta di [KeyColumn](../objects/column-element-assl.md) delle definizioni degli elementi per un oggetto padre.|  
|[Elemento KPIs &#40;ASSL&#41;](kpis-element-assl.md)|Contiene la raccolta di [Kpi](../objects/kpi-element-assl.md) elementi associati all'elemento padre.|  
|[I livelli di elemento &#40;ASSL&#41;](levels-element-assl.md)|Contiene la raccolta di [livello](../objects/level-element-assl.md) elementi in un [gerarchia](../objects/hierarchy-element-assl.md) elemento.|  
|[Elemento MdxScripts &#40;ASSL&#41;](mdxscripts-element-assl.md)|Contiene la raccolta di [MdxScript](../objects/mdxscript-element-assl.md) gli elementi associati a un [cubo](../objects/cube-element-assl.md) elemento.|  
|[Elemento MeasureGroups &#40;ASSL&#41;](measuregroups-element-assl.md)|Contiene la raccolta di [MeasureGroup](../objects/group-element-assl.md) elementi associati all'elemento padre.|  
|[Le misure di elemento &#40;ASSL&#41;](measures-element-assl.md)|Contiene la raccolta di [misura](../objects/measure-element-assl.md) elementi associati all'elemento padre.|  
|[Elemento Members &#40;ASSL&#41;](members-element-assl.md)|Contiene la raccolta di elementi [Member](../objects/member-element-assl.md) dell'elemento padre.|  
|[Elemento MiningModelPermissions &#40;ASSL&#41;](miningmodelpermissions-element-assl.md)|Contiene la raccolta di autorizzazioni per un [MiningModel](../objects/miningmodel-element-assl.md) elemento.|  
|[Elemento MiningModels &#40;ASSL&#41;](miningmodels-element-assl.md)|Contiene la raccolta di [MiningModel](../objects/miningmodel-element-assl.md) gli elementi associati a un [MiningStructure](../objects/miningstructure-element-assl.md).|  
|[Elemento MiningStructurePermissions &#40;ASSL&#41;](miningstructurepermissions-element-assl.md)|Contiene la raccolta di autorizzazioni per un [MiningStructure](../objects/miningstructure-element-assl.md) elemento.|  
|[Elemento MiningStructures &#40;ASSL&#41;](miningstructures-element-assl.md)|Contiene la raccolta di [MiningStructure](../objects/miningstructure-element-assl.md) elementi in un [Database](../objects/database-element-assl.md) elemento.|  
|[Elemento ModelingFlags &#40;ASSL&#41;](modelingflags-element-assl.md)|Contiene la raccolta di [ModelingFlag](../objects/modelingflag-element-assl.md) gli elementi per una colonna in un [MiningStructure](../objects/miningstructure-element-assl.md) o un [MiningModel](../objects/miningmodel-element-assl.md).|  
|[Elemento NamingTemplateTranslations &#40;ASSL&#41;](namingtemplatetranslations-element-assl.md)|Fornisce una raccolta di conversioni localizzate per le [NamingTemplate](../properties/namingtemplate-element-assl.md) dell'elemento padre [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md).|  
|[Suddivide l'elemento &#40;ASSL&#41;](partitions-element-assl.md)|Contiene la raccolta di [Partition](../objects/partition-element-assl.md) gli elementi utilizzati da un [MeasureGroup](../objects/group-element-assl.md) elemento o la raccolta di associazioni della partizione che costituiscono un out-of-line [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)elemento.|  
|[Elemento Perspective &#40;ASSL&#41;](perspectives-element-assl.md)|Contiene la raccolta di [prospettiva](../objects/perspective-element-assl.md) gli elementi associati a un [cubo](../objects/cube-element-assl.md) elemento.|  
|[Elemento QueryNotifications &#40;ASSL&#41;](querynotifications-element-assl.md)|Contiene la raccolta di [QueryNotification](../objects/querynotification-element-assl.md) gli elementi che forniscono informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento sulle query da eseguire per determinare se un'origine dati è stata modificata.|  
|[Elemento Reportformatparameter &#40;ASSL&#41;](reportformatparameters-element-assl.md)|Contiene la raccolta di elementi [ReportFormatParameter](../objects/reportformatparameter-element-asl.md) per un elemento [ReportAction](../data-type/action-data-type-assl.md) .|  
|[Elemento ReportParameters &#40;ASSL&#41;](reportparameters-element-assl.md)|Contiene la raccolta di [ReportParameter](../objects/reportparameter-element-assl.md) gli elementi per una [ReportAction](../data-type/action-data-type-assl.md) elemento.|  
|[Elemento Roles &#40;ASSL&#41;](roles-element-assl.md)|Contiene la raccolta di elementi [Role](../objects/role-element-assl.md) definiti all'interno dell'elemento padre.|  
|[Elemento ServerProperties &#40;ASSL&#41;](serverproperties-element-assl.md)|Contiene la raccolta di [ServerProperty](../objects/serverproperty-element-assl.md) gli elementi associati a un [Server](../objects/server-element-assl.md) elemento.|  
|[Elemento TableNotifications &#40;ASSL&#41;](tablenotifications-element-assl.md)|Contiene la raccolta di [TableNotification](../objects/tablenotification-element-assl.md) gli elementi che forniscono informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento sulle tabelle o viste in un'origine dati che sono state modificate.|  
|[Analizza l'elemento &#40;ASSL&#41;](traces-element-assl.md)|Contiene la raccolta di elementi [Trace](../objects/trace-element-assl.md) associati a un elemento [Server](../objects/server-element-assl.md).|  
|[Elemento Translations &#40;ASSL&#41;](translations-element-assl.md)|Contiene la raccolta di [traduzione](../objects/translation-element-assl.md) elementi associati all'elemento padre.|  
|[Elemento UnknownMemberTranslations &#40;ASSL&#41;](unknownmembertranslations-element-assl.md)|Contiene la raccolta di traduzioni per la didascalia del [UnknownMember](../properties/unknownmember-element-assl.md) elemento di una dimensione.|  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchia Analysis Services Scripting Language XML elemento &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
