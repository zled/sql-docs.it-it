---
title: Elemento DefaultMember (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DefaultMember Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultMember
helpviewer_keywords:
- DefaultMember element
ms.assetid: db4eea9f-f7cf-40de-abd0-b62014e7ec2d
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 71b8b2ecd1d5cd46ea50cceebe2a0105d9b7311f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068126"
---
# <a name="defaultmember-element-assl"></a>Elemento DefaultMember (ASSL)
  Contiene un'espressione MDX (Multidimensional Expression) che identifica il membro predefinito dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributePermission> <!-- or DimensionAttribute, ManyToManyMeasureGroupDimension, PerspectiveAttribute -->  
      ...  
   <DefaultMember>...</DefaultMember>  
      ...  
</AttributePermission>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[AttributePermission](../objects/attributepermission-element-assl.md), [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md), [ManyToManyMeasureGroupDimension](../data-type/dimension-data-type-assl.md), [PerspectiveAttribute](../data-type/perspectiveattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 L’elemento `DefaultMember` definisce il membro predefinito per l'elemento padre. Se `DefaultMember` non è specificato o è impostata su una stringa vuota [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sceglie un membro da utilizzare come membro predefinito.  
  
 Per gli elementi `ManyToManyMeasureGroupDimension`, l'elemento `DefaultMember` contiene un'espressione MDX che specifica un membro nella dimensione identificata nell'elemento `CubeDimensionID` di `ManyToManyMeasureGroupDimension`. L'espressione MDX è simile per la [StrToMember](/sql/mdx/strtomember-mdx) funzione MDX con la parola chiave CONSTRAINED, in quanto non può includere funzioni MDX o definite dall'utente.  
  
 Per altre informazioni, vedere [Definire un membro predefinito](../../multidimensional-models/attribute-properties-define-a-default-member.md).  
  
 Gli elementi che corrispondono ai padri di `DefaultMember` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.AttributePermission>, <xref:Microsoft.AnalysisServices.DimensionAttribute> e <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
