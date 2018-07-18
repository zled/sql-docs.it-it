---
title: Elemento binding (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c51e99c4dcfde8de6060bf57e248d32322da8ac9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37969669"
---
# <a name="binding-element-xmla"></a>Elemento Binding (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Definisce un'associazione out-of-line per un oggetto di Analysis Services, ad esempio un attributo in una dimensione, per il [associazioni](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md) raccolta di un [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) oppure [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Bindings>  
   <Binding xsi:type="DimensionAttributeBinding">...</Binding>  
   <!-- or -->  
   <Binding xsi:type="MeasureGroupAttributeBinding">...</Binding>  
   <!-- or -->  
   <Binding xsi:type="PartitionBinding">...</Binding>  
</Bindings>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[DimensionAttributeBinding](../../../analysis-services/scripting/data-type/dimensionattributebinding-data-type-out-of-line-assl.md), [MeasureGroupAttributeBinding](../../../analysis-services/scripting/data-type/measuregroupattributebinding-data-type-out-of-line-assl.md), [PartitionBinding](../../../analysis-services/scripting/data-type/partitionbinding-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Associazioni](../../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 **Binding** elementi definiscono associazioni out-of-line, diverse da origini dati e viste origine dati, per [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] gli oggetti da elaborare con un **Batch** oppure **processo** comando. Per altre informazioni sull'elaborazione degli oggetti, vedere [elaborazione di oggetti &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md).  
  
 Per altre informazioni sulle associazioni out-of-line, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
