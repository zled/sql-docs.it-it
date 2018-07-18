---
title: Elemento Role (ASSL) | Microsoft Docs
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
- Role Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ROLE
helpviewer_keywords:
- Role element
ms.assetid: 56f52462-a7fd-4b51-a7fb-4311134439e9
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0486e6f0f8cc5886c5bcab5ea389440c8d26523b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285977"
---
# <a name="role-element-assl"></a>Elemento Role (ASSL)
  Contiene informazioni su un ruolo di sicurezza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Roles>  
      <Role>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreateTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Members>...</Members>  
      <Annotations>...</Annotations>  
   </Role>  
</Roles>  
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
|Elementi padre|[Roles](../collections/roles-element-assl.md)|  
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [CreatedTimestamp](../properties/createdtimestamp-element-assl.md), [descrizione](../properties/description-element-assl.md), [ID](../properties/id-element-assl.md), [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md), [membri ](../collections/members-element-assl.md), [Nome](../properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 La definizione del ruolo include gli utenti membri del ruolo stesso.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento database &#40;ASSL&#41;](database-element-assl.md)   
 [Elemento server &#40;ASSL&#41;](server-element-assl.md)   
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
