---
title: Elemento CubePermissions (ASSL) | Microsoft Docs
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
- CubePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CubePermissions
helpviewer_keywords:
- CubePermissions element
ms.assetid: 75a3a0c2-e1d4-4896-b0f5-2ea9c769b927
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81b7e07f04c248747da81093fd3c9383665a3eb3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37178878"
---
# <a name="cubepermissions-element-assl"></a>Elemento CubePermissions (ASSL)
  Contiene la raccolta di autorizzazioni applicabili a un [cubo](../objects/cube-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube>  
   ...  
   <CubePermissions>  
      <CubePermission>...</CubePermission>  
   </CubePermissions>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cube](../objects/cube-element-assl.md)|  
|Elementi figlio|[CubePermission](../objects/cubepermission-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.CubePermissionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati Permission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
