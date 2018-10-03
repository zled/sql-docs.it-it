---
title: Elemento DatabasePermissions (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DatabasePermissions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DatabasePermissions
helpviewer_keywords:
- DatabasePermissions element
ms.assetid: c4ce0da3-f7ba-4f11-8cd8-236c32992aaf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9d92f794ecf77eabf1faf555fecb35040993937f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092171"
---
# <a name="databasepermissions-element-assl"></a>Elemento DatabasePermissions (ASSL)
  Contiene la raccolta di [DatabasePermission](../objects/databasepermission-element-assl.md) gli elementi associati a un [Database](../objects/database-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database>  
   ...  
   <DatabasePermissions>  
      <DatabasePermission>...</DatabasePermission>  
      </DatabasePermissions>  
      ...  
</Database>  
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
|Elementi padre|[Database](../objects/database-element-assl.md)|  
|Elementi figlio|[DatabasePermission](../objects/databasepermission-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DatabasePermissionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati Permission &#40;ASSL&#41;](../data-type/permission-data-type-assl.md)   
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
