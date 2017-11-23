---
title: Elemento Attributepermissions (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AttributePermission Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AttributePermission
helpviewer_keywords: AttributePermission element
ms.assetid: efc8aa63-3959-4b2e-98f8-2a9c424298c2
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b3db75bf8a3517fe9c3296036cf164979e0299e5
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="attributepermission-element-assl"></a>Elemento AttributePermissions (ASSL)
  Definisce le autorizzazioni che i membri di un [ruolo](../../../analysis-services/scripting/objects/role-element-assl.md) elemento avere gli attributi di una singola dimensione in un [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributePermissions>  
   <AttributePermission>  
      <AttributeID>...</AttributeID>  
      <Description>...</Description>  
      <DefaultMember>...</DefaultMember>  
            <VisualTotals>...</VisualTotals>  
      <AllowedSet>...</AllowedSet>  
            <DeniedSet>...</DeniedSet>  
      <Annotations>...</Annotations>  
   </AttributePermission>  
</AttributePermissions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AttributePermissions](../../../analysis-services/scripting/collections/attributepermissions-element-assl.md)|  
|Elementi figlio|[AllowedSet](../../../analysis-services/scripting/properties/allowedset-element-assl.md), [annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md), [DefaultMember](../../../analysis-services/scripting/properties/defaultmember-element-assl.md), [DeniedSet](../../../analysis-services/scripting/properties/deniedset-element-assl.md), [ Descrizione](../../../analysis-services/scripting/properties/description-element-assl.md), [VisualTotals](../../../analysis-services/scripting/properties/visualtotals-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AttributePermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati CubeDimensionPermission &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/cubedimensionpermission-data-type-assl.md)   
 [Oggetti &#40; ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
