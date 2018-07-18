---
title: Tipo di dati ProactiveCachingBinding (ASSL) | Microsoft Docs
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
- ProactiveCachingBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingBinding data type
ms.assetid: 02e6ff2f-2f18-4607-9198-bb46f113f9ac
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1d440911eefa33981ef435240c4e440378da34a4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37189098"
---
# <a name="proactivecachingbinding-data-type-assl"></a>Tipo di dati ProactiveCachingBinding (ASSL)
  Definisce un tipo di dati derivato astratto che rappresenta le informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento sulle modifiche dell'origine dati che richiedono la ricompilazione della cache o sullo stato del processo di ricompilazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCachingBinding>  
   <!-- ProactiveCachingBinding is an abstract base class with no child elements -->  
</ProactiveCachingBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Associazione](binding-data-type-assl.md)|  
|Tipi di dati derivati|[ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md), [ProactiveCachingObjectNotificationBinding](proactivecachingobjectnotificationbinding-data-type-assl.md), [ProactiveCachingQueryBinding](querybinding-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|None|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [associazione tipo di dati &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni di dati in ASSL, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ProactiveCachingBinding>.  
  
## <a name="inheritance-hierarchy-of-proactivecachingbinding-types"></a>Gerarchia di ereditarietà dei tipi ProactiveCachingBinding  
 Nella gerarchia seguente viene illustrata l'ereditarietà dei tipi `ProactiveCachingBinding`.  
  
 [Associazione](binding-data-type-assl.md) elemento  
  
 Elemento `ProactiveCachingBinding`  
  
 [ProactiveCachingObjectNotificationBinding](proactivecachingobjectnotificationbinding-data-type-assl.md) elemento  
  
 [ProactiveCachingInheritedBinding](inheritedbinding-data-type-assl.md) elemento  
  
 [ProactiveCachingTablesBinding](proactivecachingtablesbinding-data-type-assl.md) elemento  
  
 [ProactiveCachingQueryBinding](querybinding-data-type-assl.md) elemento  
  
 [ProactiveCachingIncrementalProcessingBinding](proactivecachingincrementalprocessingbinding-data-type-assl.md) elemento  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
