---
title: Elemento member (ASSL) | Microsoft Docs
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
- Member Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Member
helpviewer_keywords:
- Member element
ms.assetid: 03b4cfcb-ce87-452f-9e25-8745c0423f56
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f2d2937a4a0ec0c3608da6eb2869309ed2d4a296
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330301"
---
# <a name="member-element-assl"></a>Elemento Member (ASSL)
  Contiene il nome di un membro di un [gruppo](group-element-assl.md) elemento o di un [ruolo](role-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Members>  
   <Member>  
      <Name>...</Name>  
   </Member>  
</Members>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Membri](../collections/members-element-assl.md)|  
|Elementi figlio|[Nome](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 Gli elementi che corrispondono ai padri di `Member` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.Group> e <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
