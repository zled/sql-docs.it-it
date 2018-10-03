---
title: Tipo di dati CubeAttributeBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CubeAttributeBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubeAttributeBinding
helpviewer_keywords:
- CubeAttributeBinding data type
ms.assetid: 04e3d619-1de8-4fc8-a089-9a44ac0f930c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6b0bf386c24a27c0c02caec6d71049d6d1eb8d5e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164021"
---
# <a name="cubeattributebinding-data-type-assl"></a>Tipo di dati CubeAttributeBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta l'associazione di un attributo in una dimensione del cubo a un'azione o una colonna della struttura di data mining.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <CubeID>...</CubeID>  
   <CubeDimensionID>...</CubeDimensionID>  
      <AttributeID>...</AttributeID>  
      <Type>...</Type>  
   <Ordinal>...</Ordinal>  
</CubeAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[associazione](binding-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Elemento AttributeID](../properties/id-element-assl.md), [CubeDimensionID](../properties/dimensionid-element-assl.md), [CubeID](../properties/cubeid-element-assl.md), [ordinale](../properties/ordinal-element-assl.md), [tipo](../properties/type-element-binding-assl.md)|  
|Elementi derivati|Vedere [associazione](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [associazione tipo di dati &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni di dati in ASSL, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubeAttributeBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
