---
title: Oggetto di Analysis Services usati nelle tracce di tipi di codice | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e4119db1-4a41-4335-9b33-f1ea95564300
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7bd50f15603440953dc2f9c52ae669e5fcbd3108
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="analysis-services-object-type-codes-used-in-traces"></a>Codici del tipo di oggetto di Analysis Services usati nelle tracce
  Questa pagina elenca il tipo di oggetto (un numero di sei cifre) di ogni oggetto disponibile in un modello di dati di Analysis Services. Questi codici vengono visualizzati nei log di traccia e vengono usati per identificare il tipo di oggetto associato a un blocco specifico. Ad esempio, un timeout di blocco su un database indicherà il tipo di oggetto 100002, ovvero il tipo di oggetto Database.  
  
> [!NOTE]  
>  I codici elencati di seguito sono più numerosi rispetto a quelli effettivamente visualizzati in un log di traccia. L'elenco seguente è un elenco completo di tipi di codice per ogni oggetto, ma solo gli oggetti che accettano un blocco presenteranno un codice del tipo di oggetto in un log di traccia.  
  
## <a name="object-type-reference"></a>Informazioni di riferimento sui tipi di oggetto  
  
|Tipo oggetto|Nome oggetto|  
|-----------------|-----------------|  
|100000|Server|  
|100001|Command|  
|100002|Database|  
|100003|DataSource|  
|100004|DatabasePermission|  
|100005|Ruolo|  
|100006|Dimensione|  
|100007|DimensionAttribute|  
|100008|Gerarchia|  
|100009|Level|  
|100010|Cube|  
|100011|CubePermission|  
|100012|CubeDimension|  
|100013|CubeAttribute|  
|100014|CubeHierarchy|  
|100016|MeasureGroup|  
|100017|MeasureGroupDimension|  
|100018|MeasureGroupAttribute|  
|100020|Misura|  
|100021|Partition|  
|100025|AggregationDesign|  
|100026|AggregationDesignDimension|  
|100027|AggregationDesignAttribute|  
|100028|Aggregazione|  
|100029|AggregationDimension|  
|100030|AggregationAttribute|  
|100032|MiningStructure|  
|100033|MiningStructureColumn|  
|100037|MiningModel|  
|100038|MiningModelColumn|  
|100039|AlgorithmParameters|  
|100041|MiningModelPermission|  
|100042|DimensionPermission|  
|100043|MiningStructurePermission|  
|100044|Assembly|  
|100045|DatabaseRole|  
|100046|AttributePermission|  
|100047|CubeAttributePermission|  
|100048|CellPermission|  
|100049|CubeDimensionPermission|  
|100050|Traccia|  
|100051|ServerAssembly|  
|100052|CubeAssembly|  
|100053|Command|  
|100054|Indicatore KPI|  
|100055|DataSourceView|  
|100056|Prospettiva|  
|100100|CommandCollection|  
|100101|DatabaseCollection|  
|100102|DataSourceCollection|  
|100103|DatabasePermission|  
|100104|RoleCollection|  
|100105|DimensionCollection|  
|100106|DimensionAttributeCollection|  
|100107|HierarchyCollection|  
|100108|LevelCollection|  
|100109|CubeCollection|  
|100110|CubePermissionCollection|  
|100111|CubeDimensionCollection|  
|100112|CubeAttributeCollection|  
|100113|CubeHierarchyCollection|  
|100115|MeasureGroupCollection|  
|100116|MeasureGroupDimensionCollection|  
|100117|MeasureGroupAttributeCollection|  
|100119|MeasureCollection|  
|100120|PartitionCollection|  
|100124|AggregationDesignCollection|  
|100125|AggregationDesignDimensionCollection|  
|100126|AggregationDesignAttributeCollection|  
|100127|AggregationCollection|  
|100128|AggregationDimensionCollection|  
|100129|AggregationAttributeCollection|  
|100131|MiningStructureCollection|  
|100132|MiningStructureColumnCollection|  
|100136|MiningModelCollection|  
|100137|MiningModelColumnCollection|  
|100138|AlgorithmParameterCollection|  
|100140|MiningModelPermissionCollection|  
|100141|DimensionPermissionCollection|  
|100142|MiningStructurePermissionCollection|  
|100143|AssemblyCollection|  
|100144|DatabaseRoleCollecction|  
|100145|AttributePermissionCollection|  
|100146|CubeAttributePermissionCollection|  
|100147|CellPermissionCollection|  
|100148|CubeDimensionPermissionCollection|  
|100149|TraceCollection|  
|100150|ServerAssemblyCollection|  
|100151|CubeAssemblyCollection|  
|100152|CommandCollection|  
|100153|KpiCollection|  
|100154|DataSourceViewCollection|  
|100155|PerspectiveCollection|  
  
  

