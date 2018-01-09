---
title: Il recupero dei metadati da un'origine dati analitici | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- metadata [ADOMD.NET]
- retrieving metadata
ms.assetid: 00043ebd-7164-4ceb-b945-6e44378ea00a
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1ccc559449edeb5274c22aa892c21a4677f75f61
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="retrieving-metadata-from-an-analytical-data-source"></a>Recupero di metadati da un'origine dati analitici
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]I metadati sono importanti per le applicazioni che recuperano e utilizzano con i dati analitici. Quando si recuperano dati da un'origine dati relazionale, la dimensionalità di tali dati è stimabile, anche con i set di dati nidificati. Sebbene la struttura dei set di risultati da un database relazionale sia in genere bidimensionale o scalare, i dati recuperati dalle origini dati analitici possono essere tuttavia di dimensioni variabili, organizzati in gerarchie con numerosi livelli potenziali.  
  
 Per gestire la complessità del recupero di metadati dalle origini dati analitici, in ADOMD.NET è possibile recuperare metadati in due modi diversi:  
  
 **Il modello a oggetti**  
 Il modello a oggetti ADOMD.NET è in genere più semplice da utilizzare rispetto ai set di righe dello schema. Per la maggior parte degli scenari, per accedere ai metadati di vari oggetti di database è sufficiente utilizzare il modello a oggetti. ADOMD.NET espone il modello a oggetti tramite <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>.  
  
 Per ulteriori informazioni: [utilizzano il modello a oggetti ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-adomd-net-object-model.md)  
  
 **Set di righe dello schema**  
 Un approccio completo, ma più complesso, per il recupero di metadati è costituito dai set di righe dello schema. Un set di righe dello schema è un set di righe OLE DB che incapsula la descrizione di tutti gli oggetti di un tipo specifico del database. Le informazioni sullo schema in un'origine dati analitici includono i database oppure i cataloghi disponibili dall'origine dati, i cubi e modelli di data mining in un database, i ruoli che esistono per i cubi nell'origine dati e così via. Questi metadati possono essere recuperato tramite il <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.GetSchemaDataSet%2A> (metodo), passando un **GUID** o un file XML per il nome Analysis (XMLA).  
  
 Per ulteriori informazioni: [Working with Schema Rowsets in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)  
  
 Ciascuno di questi metodi per il recupero di metadati accede a tipi diversi di metadati. Nella tabella seguente vengono descritti i metadati diversi disponibili per ogni metodo e i metodi utilizzati per accedervi.  
  
|GUID (utilizzato nei set di righe dello schema)|Nome XMLA (utilizzato nei set di righe dello schema)|Modello a oggetti ADOMD.NET|  
|-------------------------------------|------------------------------------------|----------------------------|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Actions>|[Set di righe MDSCHEMA_ACTIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Catalogs>|[Set di righe DBSCHEMA_CATALOGS](../../analysis-services/schema-rowsets/ole-db/dbschema-catalogs-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Columns>|[Set di righe DBSCHEMA_COLUMNS](../../analysis-services/schema-rowsets/ole-db/dbschema-columns-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Connections>|**DISCOVER_CONNECTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Cubes>|[Set di righe MDSCHEMA_CUBES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|AdomdConnection.Cubes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DataSources>|[Set di righe DISCOVER_DATASOURCES](../../analysis-services/schema-rowsets/xml/discover-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DBConnections>|**DISCOVER_DB_CONNECTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Dimensions>|[Set di righe MDSCHEMA_DIMENSIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|AdomdConnection.Cubes[].Dimensions|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.DimensionStat>|**DISCOVER_DIMENSION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Enumerators>|[Set di righe DISCOVER_ENUMERATORS](../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Functions>|[Set di righe MDSCHEMA_FUNCTIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Hierarchies>|[Set di righe MDSCHEMA_HIERARCHIES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.InputDataSources>|[Set di righe MDSCHEMA_INPUT_DATASOURCES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Instances>|[Set di righe DISCOVER_INSTANCES](../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Jobs>|**DISCOVER_JOBS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Keywords>|[Set di righe DISCOVER_KEYWORDS &#40; OLE DB per OLAP &#41;](../../analysis-services/schema-rowsets/ole-db-olap/discover-keywords-rowset-ole-db-for-olap.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Kpis>|[Set di righe MDSCHEMA_KPIS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|AdomdConnection.Cubes[].KPIs|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Levels>|[Set di righe MDSCHEMA_LEVELS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies[].Levels|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Literals>|[Set di righe DISCOVER_LITERALS](../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locations>|**DISCOVER_LOCATIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Locks>|**DISCOVER_LOCKS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MasterKey>|**DISCOVER_MASTER_KEY**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroupDimensions>|[Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MeasureGroups>|[Set di righe MDSCHEMA_MEASUREGROUPS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Measures>|[Set di righe MDSCHEMA_MEASURES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|AdomdConnection.Cubes[].Measures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemberProperties>|[Set di righe MDSCHEMA_PROPERTIES](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|PropertyCollection disponibile nella maggior parte degli oggetti ADOMD.NET principali.|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Members>|[Set di righe MDSCHEMA_MEMBERS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|AdomdConnection.Cubes[].Dimensions[].Hierarchies[].Levels[].GetMembers()|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryGrant>|**DISCOVER_MEMORYGRANT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MemoryUsage>|**DISCOVER_MEMORYUSAGE**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningColumns>|[Set di righe DMSCHEMA_MINING_COLUMNS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-columns-rowset.md)|AdomdConnection.MiningModels[].MiningModelColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningFunctions>|[Set di righe DMSCHEMA_MINING_FUNCTIONS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-functions-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContent>|[Set di righe DMSCHEMA_MINING_MODEL_CONTENT](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md)|AdomdConnection.MiningModels[].MiningContentNodes|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelContentPmml>|[Set di righe DMSCHEMA_MINING_MODEL_CONTENT_PMML](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-pmml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModels>|[Set di righe DMSCHEMA_MINING_MODELS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-models-rowset.md)|AdomdConnection.MiningModels|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningModelXml>|[Set di righe DMSCHEMA_MINING_MODEL_XML](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-xml-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServiceParameters>|[Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)|AdomdConnection.MiningServices[].MiningServiceParameters|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningServices>|[Set di righe DMSCHEMA_MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)|AdomdConnection.MiningServices|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructureColumns>|[Set di righe DMSCHEMA_MINING_STRUCTURE_COLUMNS](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structure-columns-rowset.md)|AdomdConnection.MiningStructures[].MiningStructureColumns|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.MiningStructures>|[Set di righe DMSCHEMA_MINING_STRUCTURES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-structures-rowset.md)|AdomdConnection.MiningStructures|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionDimensionStat>|**DISCOVER_PARTITION_DIMENSION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PartitionStat>|**DISCOVER_PARTITION_STAT**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.PerformanceCounters>|**DISCOVER_PERFORMANCE_COUNTERS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.ProviderTypes>|[Set di righe DBSCHEMA_PROVIDER_TYPES](../../analysis-services/schema-rowsets/ole-db/dbschema-provider-types-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.SchemaRowsets>|[Set di righe DISCOVER_SCHEMA_ROWSETS](../../analysis-services/schema-rowsets/xml/discover-schema-rowsets-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sessions>|**DISCOVER_SESSIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Sets>|[Set di righe MDSCHEMA_SETS](../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|AdomdConnection.Cubes[].NamedSets|  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Tables>|[Set di righe DBSCHEMA_TABLES](../../analysis-services/schema-rowsets/ole-db/dbschema-tables-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TablesInfo>|**DBSCHEMA_TABLES_INFO**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceColumns>|**DISCOVER_TRACE_COLUMNS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceDefinitionProviderInfo>|**DISCOVER_TRACE_DEFINITION_PROVIDERINFO**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.TraceEventCategories>|**DISCOVER_TRACE_EVENT_CATEGORIES**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Traces>|**DISCOVER_TRACES**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.Transactions>|**DISCOVER_TRANSACTIONS**||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlaProperties>|[Set di righe DISCOVER_PROPERTIES](../../analysis-services/schema-rowsets/xml/discover-properties-rowset.md)||  
|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdSchemaGuid.XmlMetadata>|[Set di righe DISCOVER_XML_METADATA](../../analysis-services/schema-rowsets/xml/discover-xml-metadata-rowset.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione di Client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Programmazione di Client ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)   
 [Set di righe dello schema di Analysis Services](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
