---
title: Elemento AutoRestart (ASSL) | Microsoft Docs
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
- AutoRestart Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AutoRestart
helpviewer_keywords:
- AutoRestart element
ms.assetid: 4c6a0e40-8e13-4d63-bf98-9470ffe95d02
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecb6893c7c3e87c9e96890a917bbe8aad540433d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159102"
---
# <a name="autorestart-element-assl"></a>Elemento AutoRestart (ASSL)
  Determina se un [traccia](../objects/trace-element-assl.md) elemento deve riavviarsi automaticamente quando il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] servizio sarà arrestato e riavviato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Trace>  
   ...  
   <AutoRestart>...</AutoRestart>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|`False`|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Traccia](../objects/trace-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento che corrisponde al padre di `AutoRestart` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Trace>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analizza l'elemento &#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
