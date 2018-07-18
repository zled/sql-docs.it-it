---
title: Elemento StorageMode (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 72b2963293c6c59338ad23f8e4f4f5c0e9d19001
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34038655"
---
# <a name="storagemode-element-assl"></a>Elemento StorageMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Determina la modalità di archiviazione per l’elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <StorageMode>...</StorageMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*MOLAP*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Elemento del cubo &#40;ASSL&#41;](../../../analysis-services/scripting/objects/cube-element-assl.md), [dimensione elemento &#40;ASSL&#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md), [elemento MeasureGroup &#40;ASSL&#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [partizione Elemento &#40;ASSL&#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*MOLAP*|L'elemento padre utilizza l'archiviazione OLAP multidimensionale (MOLAP).|  
|*ROLAP*|L'elemento padre utilizza l'archiviazione OLAP relazionale (ROLAP).|  
|*HOLAP*|L'elemento padre utilizza l'archiviazione OLAP ibrido (HOLAP).<br /><br /> Nota: Questo valore non è valido per [dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md) gli elementi padre.|  
|*InMemory*|L'elemento padre utilizza l'archiviazione IMBI.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **StorageMode** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.StorageMode>.  
  
 Gli elementi che corrispondono ai padri di **StorageMode** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, e <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
