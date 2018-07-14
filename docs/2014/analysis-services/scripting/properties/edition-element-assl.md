---
title: Elemento Edition (ASSL) | Microsoft Docs
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
- Edition Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Edition
helpviewer_keywords:
- Edition element
ms.assetid: 521e1286-097e-494f-b036-61047096e87e
caps.latest.revision: 38
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8a94ed085a345100579b3305fa43e7e360fe8258
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37245661"
---
# <a name="edition-element-assl"></a>Elemento Edition (ASSL)
  Contiene l'edizione di sola lettura dell'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rappresentato dalle [Server](../objects/server-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Server>  
      ...  
      <Edition>...</Edition>  
   ...  
</Server>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Server](../objects/server-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `Edition` descrive l'edizione di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] installata. Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Standard*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Standard edition per processori a 32 bit.|  
|*Enterprise*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enterprise edition per processori a 32 bit.|  
|*EnterpriseCore*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Edizione Enterprise: licenze basate su Core per processori a 32 bit.|  
|*BusinessIntelligence*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Business Intelligence edition per processori a 32 bit.|  
|*Per gli sviluppatori*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Developer edition per processori a 32 bit|  
|*Valutazione*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Evaluation edition per processori a 64 bit.|  
|*Locale*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Local edition per processori a 32 bit.|  
|*Standard64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Standard edition per processori a 64 bit.|  
|*Enterprise64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Enterprise edition per processori a 64 bit.|  
|*EnterpriseCore64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Edizione Enterprise: licenze basate su Core per processori a 64 bit.|  
|*BusinessIntelligence64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Business Intelligence edition per processori a 64 bit.|  
|*Developer64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Developer edition per processori a 64 bit|  
|*Evaluation64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Evaluation edition per processori a 64 bit.|  
|*Local64*|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Local edition per processori a 64 bit.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `ServerEdition` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.ServerEdition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Version &#40;ASSL&#41;](version-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
