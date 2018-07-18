---
title: Tipo di dati ProactiveCachingIncrementalProcessingBinding (ASSL) | Microsoft Docs
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
- ProactiveCachingIncrementalProcessingBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingIncrementalProcessingBinding data type
ms.assetid: f49c0c96-4277-417b-9660-d77a4faebd00
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad1107d1ad2e135e65b2ef4f05fd2e85d799123c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247721"
---
# <a name="proactivecachingincrementalprocessingbinding-data-type-assl"></a>Tipo di dati ProactiveCachingIncrementalProcessingBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta un'associazione per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento sullo stato del processo di ricompilazione della cache.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCachingIncrementalProcessingBinding>  
   <!-- The following elements extend ProactiveCachingBinding -->  
   <RefreshInterval>...</ RefreshInterval >  
   <IncrementalProcessingNotification>...</ IncrementalProcessingNotification >  
</ProactiveCachingIncrementalProcessingBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[ProactiveCachingBinding](binding-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md), [RefreshInterval](../properties/refreshinterval-element-assl.md)|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sul `ProactiveCachingBinding` tipo, inclusa una tabella della gerarchia di ereditarietà di `ProactiveCachingBinding` tipi, vedere [tipo di dati ProactiveCachingBinding &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Per altre informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [associazione tipo di dati &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni di dati in ASSL, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ProactiveCachingIncrementalProcessingBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
