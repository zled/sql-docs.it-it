---
title: Elemento ID (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 398520b30a26e4e7d76737ff5082bbcd4d80004c
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="id-element-assl"></a>Elemento ID (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene l'identificatore univoco (ID) dell’elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action> <!-- or one of the elements listed in the Element Relationships table -->  
   ...  
   <ID>...</ID>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Stringa (fino a 100 caratteri)|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md), [aggregazione](../../../analysis-services/scripting/objects/aggregation-element-assl.md), [AggregationDesign](../../../analysis-services/scripting/objects/aggregationdesign-element-assl.md), [Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md), [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md), [CubeBinding](../../../analysis-services/scripting/data-type/cubebinding-data-type-out-of-line-assl.md), [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md), [Database](../../../analysis-services/scripting/objects/database-element-assl.md), [DataSource](../../../analysis-services/scripting/objects/datasource-element-assl.md), [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md), [dimensione ](../../../analysis-services/scripting/objects/dimension-element-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [gerarchia](../../../analysis-services/scripting/objects/hierarchy-element-assl.md), [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md), [livello](../../../analysis-services/scripting/objects/level-element-assl.md), [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md), [Misura](../../../analysis-services/scripting/objects/measure-element-assl.md), [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-assl.md), [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [ MiningModelColumn](../../../analysis-services/scripting/data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md), [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md), [partizione](../../../analysis-services/scripting/objects/partition-element-assl.md), [autorizzazione](../../../analysis-services/scripting/data-type/permission-data-type-assl.md), [Prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md), [ruolo](../../../analysis-services/scripting/objects/role-element-assl.md), [Server](../../../analysis-services/scripting/objects/server-element-assl.md), [traccia](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Ogni oggetto principale in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ha un **ID** elemento come una proprietà. Il valore di un **ID** elemento presenta le restrizioni seguenti:  
  
-   Il valore non deve contenere spazi iniziali o finali. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rimuoveranno implicitamente gli spazi iniziali o finali dal valore di un **ID** elemento.  
  
-   Il valore non può contenere caratteri di controllo. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rimuoveranno implicitamente i caratteri di controllo dal valore di un **ID** elemento.  
  
-   Impossibile utilizzare i seguenti valori riservati:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 tramite COM9 (COM1, COM2, COM3 e così via)  
  
    -   CON  
  
    -   LPT1 tramite LPT9 (LPT1, LPT2, LPT3 e così via)  
  
    -   NUL  
  
    -   PRN  
  
 Nella tabella seguente sono elencati caratteri aggiuntivi che non possono essere utilizzati all'interno del valore di un **ID** elemento, a seconda dell'elemento padre.  
  
|Elemento padre|Caratteri|  
|--------------------|----------------|  
|[Server](../../../analysis-services/scripting/objects/server-element-assl.md)|Il valore deve seguire le regole per [!INCLUDE[msCoName](../../../includes/msconame-md.md)] i nomi del computer di Windows. (Gli indirizzi IP non sono validi)|  
|[Origine dati](../../../analysis-services/scripting/objects/datasource-element-assl.md)|:/\\*&#124;?" [] (){}<>|  
|[Livello](../../../analysis-services/scripting/objects/level-element-assl.md), [attributi elemento](../../../analysis-services/scripting/objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! + = []{}<>|  
|Tutti gli altri elementi padre|.,;' `:/\\*&#124;?" & % $! [] () + ={}<>|  
  
## <a name="see-also"></a>Vedere anche  
 [Nome di elemento &#40;ASSL&#41;](../../../analysis-services/scripting/properties/name-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
