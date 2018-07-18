---
title: Elemento ID (ASSL) | Microsoft Docs
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
api_name:
- ID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ID
helpviewer_keywords:
- ID element
ms.assetid: ea3ce0f4-9084-45d0-8150-73afb7005af2
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c323bd71865d0dd09bf724373ece03d83e7608ee
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37209941"
---
# <a name="id-element-assl"></a>Elemento ID (ASSL)
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
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Stringa (fino a 100 caratteri)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Azione](../objects/action-element-assl.md), [aggregazione](../objects/aggregation-element-assl.md), [AggregationDesign](../objects/aggregationdesign-element-assl.md), [Assembly](../objects/assembly-element-assl.md), [cubo](../objects/cube-element-assl.md), [CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md), [CubeDimension](../data-type/dimension-data-type-assl.md), [Database](../objects/database-element-assl.md), [DataSource](../objects/datasource-element-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [dimensione ](../objects/dimension-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [gerarchia](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [livello](../objects/level-element-assl.md), [MdxScript](../objects/mdxscript-element-assl.md), [Misura](../objects/measure-element-assl.md), [MeasureGroup](../objects/group-element-assl.md), [MeasureGroupBinding](../data-type/binding-data-type-assl.md), [MiningModel](../objects/miningmodel-element-assl.md), [ MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md), [MiningStructure](../objects/miningstructure-element-assl.md), [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md), [partizione](../objects/partition-element-assl.md), [autorizzazione](../data-type/permission-data-type-assl.md), [Prospettiva](../objects/perspective-element-assl.md), [ruolo](../objects/role-element-assl.md), [Server](../objects/server-element-assl.md), [traccia](../objects/trace-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Ogni oggetto principale nel [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ha un `ID` elemento rappresenta una proprietà. Il valore di un elemento `ID` ha le seguenti restrizioni:  
  
-   Il valore non deve contenere spazi iniziali o finali. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rimuoveranno in modo implicito spazi iniziali o finali dal valore di un elemento `ID`.  
  
-   Il valore non può contenere caratteri di controllo. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rimuoveranno implicitamente i caratteri di controllo dal valore di un elemento `ID`.  
  
-   Impossibile utilizzare i seguenti valori riservati:  
  
    -   AUX  
  
    -   CLOCK$  
  
    -   COM1 tramite COM9 (COM1, COM2, COM3 e così via)  
  
    -   CON  
  
    -   LPT1 tramite LPT9 (LPT1, LPT2, LPT3 e così via)  
  
    -   NUL  
  
    -   PRN  
  
 Nella tabella seguente sono elencati caratteri aggiuntivi che non possono essere utilizzati all'interno del valore di un elemento `ID`, a seconda dell'elemento padre.  
  
|Elemento padre|Caratteri|  
|--------------------|----------------|  
|[Server](../objects/server-element-assl.md)|Il valore deve seguire le regole per [!INCLUDE[msCoName](../../../includes/msconame-md.md)] i nomi del computer di Windows. (Gli indirizzi IP non sono validi)|  
|[Origine dati](../objects/datasource-element-assl.md)|:/\\*&#124;?" [] (){}<>|  
|[Livello](../objects/level-element-assl.md), [attributo a elemento](../objects/attribute-element-assl.md)|.,;' `:/\\*&#124;?" & % $! + = []{}<>|  
|Tutti gli altri elementi padre|.,;' `:/\\*&#124;?" & % $! + = [] (){}<>|  
  
## <a name="see-also"></a>Vedere anche  
 [Denominare l'elemento &#40;ASSL&#41;](name-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
