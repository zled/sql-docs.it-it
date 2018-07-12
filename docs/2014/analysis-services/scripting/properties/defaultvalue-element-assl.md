---
title: Elemento DefaultValue (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DefaultValue Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DefaultValue
helpviewer_keywords:
- DefaultValue element
ms.assetid: 87e964a3-f317-46c3-98c7-b3621765c77b
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f4137e73097630d62358ea874a38afda6d90eb87
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37277847"
---
# <a name="defaultvalue-element-assl"></a>Elemento DefaultValue (ASSL)
  Contiene il valore predefinito di sola lettura dell'oggetto associato [ServerProperty](../objects/serverproperty-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ServerProperty>  
   ...  
   <DefaultValue>   </DefaultValue>  
   ...  
</ServerProperty>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Any simpleType|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[ServerProperty](../objects/serverproperty-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Questo elemento contiene il valore predefinito di installazione di sola lettura dei `ServerProperty` per l'istanza corrente di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Il valore predefinito è fornito dall'istanza e in genere non può essere modificato.  
  
 L'elemento che corrisponde al padre di `DefaultValue` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ServerProperties &#40;ASSL&#41;](../collections/serverproperties-element-assl.md)   
 [Elemento server &#40;ASSL&#41;](../objects/server-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
