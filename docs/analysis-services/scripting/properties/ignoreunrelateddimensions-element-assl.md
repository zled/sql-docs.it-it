---
title: Elemento IgnoreUnrelatedDimensions (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fb55ec97bc6ca2e619e04b43b1e56869c57db5b2
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34034662"
---
# <a name="ignoreunrelateddimensions-element-assl"></a>Elemento IgnoreUnrelatedDimensions (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Determina se le dimensioni non correlate devono essere forzate al livello principale in caso di inclusione in una query di membri di dimensioni non correlate al gruppo di misure.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|True|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Gruppo di misure](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Quando **IgnoreUnrelatedDimensions** è **true**, le dimensioni non correlate sono forzate al livello superiore; quando il valore è **false**, le dimensioni non sono forzate al livello superiore. Questa proprietà è simile a espressioni MDX (Multidimensional) [ValidMeasure](../../../mdx/validmeasure-mdx.md) (funzione).  
  
 L'elemento che corrisponde all'elemento padre **IgnoreUnrelatedDimensions** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MeasureGroup>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
