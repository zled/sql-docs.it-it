---
title: Elemento CubePermission (ASSL) | Documenti Microsoft
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
- CubePermission Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CubePermission
helpviewer_keywords:
- CubePermission element
ms.assetid: b144b623-ff20-4ead-91ad-4c718f3b140b
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2cc725b59d221d447f257677f5491a8e6829681a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="cubepermission-element-assl"></a>Elemento CubePermission (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce le autorizzazioni dei membri di un particolare [ruolo](../../../analysis-services/scripting/objects/role-element-assl.md) in uno specifico elemento [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubePermissions>  
   <CubePermission>  
      <!-- The following elements extend Permission -->  
      <ReadSourceData>...</ReadSourceData>  
            <DimensionPermissions>...</DimensionPermissions>  
            <CellPermissions>...</CellPermissions>  
   </CubePermission>  
</CubePermissions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|[Autorizzazione](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CubePermissions](../../../analysis-services/scripting/collections/cubepermissions-element-assl.md)|  
|Elementi figlio|[CellPermissions](../../../analysis-services/scripting/collections/cellpermissions-element-assl.md), [DimensionPermissions](../../../analysis-services/scripting/collections/dimensionpermissions-element-assl.md), [ReadSourceData](../../../analysis-services/scripting/properties/readsourcedata-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubePermission>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CUBE & #40; ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
