---
title: Elemento ForeignKeyColumn (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- ForeignKeyColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ForeignKeyColumn
helpviewer_keywords:
- ForeignKeyColumn element
ms.assetid: 6c00dcc6-8d5b-4293-8b72-c7a22e298c8d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f4688ac6efd03e10b5950abcbcc0da99a1cbc5b6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48149791"
---
# <a name="foreignkeycolumn-element-assl"></a>Elemento ForeignKeyColumn (ASSL)
  Identifica il join a una tabella padre per un'origine dati relazionale.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ForeignKeyColumns>  
   <ForeignKeyColumn xsi:type="DataItem">...</ForeignKeyColumn>  
</ForeignKeyColumns>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ForeignKeyColumns](../collections/columns-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sul `DataItem` tipo, inclusa una tabella di oggetti di Analysis Services Scripting Language (ASSL) e le proprietà del `DataItem` del tipo, vedere [tipo di dati DataItem &#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md).  
  
 L’elemento che corrisponde al padre della raccolta `ForeignKeyColumns` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati TableMiningStructureColumn &#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [Tipo di dati MiningStructureColumn &#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [Elemento MiningStructure &#40;ASSL&#41;](miningstructure-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
