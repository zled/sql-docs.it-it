---
title: Partizioni di elemento (ASSL) | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2faa85cb0caa87e537fc66f3385e574559d00ce2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34029022"
---
# <a name="partitions-element-assl"></a>Elemento Partitions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la raccolta di [partizione](../../../analysis-services/scripting/objects/partition-element-assl.md) gli elementi utilizzati da un [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md) elemento o la raccolta di associazioni della partizione che costituiscono un out-of-line [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroup> <!-- or MeasureGroupBinding -->  
   ...  
   <Partitions>  
      <Partition>...</Partition> <!-- parent: MeasureGroup -->  
      <!-- or -->  
      <Partition xsi:type="PartitionBinding">...</Partition> <!-- parent: MeasureGroupBinding -->  
   </Partitions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Elemento figlio|  
|------------------------|-------------------|  
|[Gruppo di misure](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|[Partizione](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|[MeasureGroupBinding](../../../analysis-services/scripting/data-type/measuregroupbinding-data-type-out-of-line-assl.md)|[Partizione](../../../analysis-services/scripting/objects/partition-element-assl.md) di tipo [PartitionBinding](../../../analysis-services/scripting/data-type/partitionbinding-data-type-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.PartitionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
