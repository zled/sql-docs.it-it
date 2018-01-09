---
title: Elemento DimensionPermission (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DimensionPermission Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DimensionPermission
helpviewer_keywords: DimensionPermission element
ms.assetid: e06efbda-64fd-4dca-a2b5-c8ffbf21512c
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7e15c2d5d155a14b71a08185123495bc9ba535f1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="dimensionpermission-element-assl"></a>Elemento DimensionPermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Definisce le autorizzazioni che appartengono a un determinato [ruolo](../../../analysis-services/scripting/objects/role-element-assl.md) elemento per una dimensione di database specifico o una dimensione del cubo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionPermissions>  
   <DimensionPermission xsi:type="DimensionPermission">...</DimensionPermission> <!-- ancestor: Dimension -->  
   <!-- or -->  
   <DimensionPermission xsi:type="CubeDimensionPermission">...</DimensionPermission> <!-- ancestor: CubePermission -->  
</DimensionPermissions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Di seguito sono valide padre (o predecessore): coppie di tipo di dati:<br /><br /> [Dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md):[DimensionPermission](../../../analysis-services/scripting/data-type/dimensionpermission-data-type-assl.md)<br /><br /> [CubePermission](../../../analysis-services/scripting/objects/cubepermission-element-assl.md):<br />                        [CubeDimensionPermission](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md)|  
|Valore predefinito|None|  
|Cardinalità|0-n: elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionPermissions](../../../analysis-services/scripting/collections/dimensionpermissions-element-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.DimensionPermission> e <xref:Microsoft.AnalysisServices.CubeDimensionPermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
