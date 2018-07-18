---
title: Elemento DefaultMeasure (ASSL) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 680d077bd053ed212ecc2c3f330b09784bc755df
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34030312"
---
# <a name="defaultmeasure-element-assl"></a>Elemento DefaultMeasure (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene un'espressione MDX (Multidimensional Expressions) che definisce la misura predefinita per un [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) o [prospettiva](../../../analysis-services/scripting/objects/perspective-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or Perspective -->  
   ...  
   <DefaultMeasure>...</DefaultMeasure>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Cube](../../../analysis-services/scripting/objects/cube-element-assl.md), [Perspective](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi che corrispondono ai padri di **DefaultMeasure** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.Cube> e <xref:Microsoft.AnalysisServices.Perspective>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
