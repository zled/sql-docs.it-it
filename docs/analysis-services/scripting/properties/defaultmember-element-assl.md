---
title: Elemento DefaultMember (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d050c0cb2209c855da35a7f1afd2fe028575edf7
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="defaultmember-element-assl"></a>Elemento DefaultMember (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[AttributePermission](../../../analysis-services/scripting/objects/attributepermission-element-assl.md), [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md), [PerspectiveAttribute](../../../analysis-services/scripting/data-type/perspectiveattribute-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **DefaultMember** elemento definisce il membro predefinito per l'elemento padre. Se **DefaultMember** non è specificato o è impostata su una stringa vuota, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sceglie un membro da utilizzare come membro predefinito.  
  
 Per **ManyToManyMeasureGroupDimension** elementi, il **DefaultMember** elemento contiene un'espressione MDX che specifica un membro nella dimensione identificata nel **CubeDimensionID**  elemento il **ManyToManyMeasureGroupDimension**. L'espressione MDX è simile al [StrToMember](../../../mdx/strtomember-mdx.md) funzione MDX con la parola chiave CONSTRAINED, in quanto non può includere funzioni MDX o definite dall'utente.  
  
 Per altre informazioni, vedere [Definire un membro predefinito](../../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md).  
  
 Gli elementi che corrispondono ai padri di **DefaultMember** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.AttributePermission>, <xref:Microsoft.AnalysisServices.DimensionAttribute>, e <xref:Microsoft.AnalysisServices.PerspectiveAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
