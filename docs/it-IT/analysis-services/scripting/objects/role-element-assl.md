---
title: Elemento Role (ASSL) | Documenti Microsoft
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
- Role Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ROLE
helpviewer_keywords:
- Role element
ms.assetid: 56f52462-a7fd-4b51-a7fb-4311134439e9
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 597892993b4c232c2eb342fcf68653f58e2c75c5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="role-element-assl"></a>Elemento Role (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Roles](../../../analysis-services/scripting/collections/roles-element-assl.md)|  
|Elementi figlio|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md), [descrizione](../../../analysis-services/scripting/properties/description-element-assl.md), [ID](../../../analysis-services/scripting/properties/id-element-assl.md), [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md), [membri ](../../../analysis-services/scripting/collections/members-element-assl.md), [Nome](../../../analysis-services/scripting/properties/name-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 La definizione del ruolo include gli utenti membri del ruolo stesso.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.Role>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento database &#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [Elemento server & #40; ASSL & #41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [Oggetti & #40; ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
