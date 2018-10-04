---
title: Elemento member (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Member Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Member
- microsoft.xml.analysis.member
- http://schemas.microsoft.com/analysisservices/2003/engine#Member
helpviewer_keywords:
- Member element
ms.assetid: 5cc33a1f-192e-4821-a4ef-9a5f2bb7a9f0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8ab24b02a46a5e6416018d9f77c733b0d3de7153
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168971"
---
# <a name="member-element-xmla"></a>Elemento Member (XMLA)
  Rappresenta un singolo membro in un elemento padre [membri](members-element-xmla.md) oppure [tupla](tuple-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Members>  
   ...  
   <Member>  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Members>  
<!-- or -->  
<Tuple>  
   ...  
   <Member Hierarchy="string">  
      <UName>...</UName>  
      <Caption>...</Caption>  
      <LName>...</LName>  
      <LNum>...</LNum>  
      <DisplayInfo>...</DisplayInfo>  
   </Member>  
   ...  
</Tuple>  
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
|Elementi padre|[I membri](members-element-xmla.md), [tupla](tuple-element-xmla.md)|  
|Elementi figlio|[Didascalia](caption-element-xmla.md), [DisplayInfo](displayinfo-element-xmla.md), [LName](name-element-xmla.md), [LNum](lnum-element-xmla.md), [UName](uname-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|Gerarchia|Attributo `String` obbligatorio (solo per gli elementi padre `Tuple`). Nome della gerarchia a cui appartiene il membro rappresentato dall'elemento `Member`.|  
  
## <a name="remarks"></a>Note  
 L'elemento `Member` contiene le informazioni necessarie per identificare e visualizzare un membro in una gerarchia specifica. Per gli elementi padre `Members`, la gerarchia è già specificata dall'attributo `Hierarchy` dell'elemento padre. Per gli elementi padre `Tuple`, la gerarchia viene specificata tramite l'attributo `Hierarchy` dell'elemento `Member`.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
