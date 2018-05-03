---
title: Elemento AttributeHierarchyVisible (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AttributeHierarchyVisible Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AttributeHierarchyVisible
helpviewer_keywords:
- AttributeHierarchyVisible element
ms.assetid: a3289a9a-dbd6-43e8-a7ca-ee8a1da92a32
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b6d0a67ec3e2f91a0b8567bd0e4476d7ee7275f9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="attributehierarchyvisible-element-assl"></a>Elemento AttributeHierarchyVisible (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Determina se la gerarchia dell'attributo è visibile alle applicazioni client.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute or PerspectiveAttribute -->  
   ...  
   <AttributeHierarchyVisible>...</AttributeHierarchyVisible>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|**True**|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **AttributeHierarchyVisible** elemento determina se la gerarchia dell'attributo associata con l'attributo è visibile alle applicazioni client. Se questo elemento è impostato su **False**, la gerarchia dell'attributo può comunque essere utilizzata per creare gerarchie definite dall'utente e a cui fa riferimento tramite istruzioni MDX (Multidimensional Expressions).  
  
 Gli elementi che corrispondono ai padri di **AttributeHierarchyVisible** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.CubeAttribute>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, e <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento AttributeHierarchyEnabled &#40;ASSL&#41;](../../../analysis-services/scripting/properties/attributehierarchyenabled-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
