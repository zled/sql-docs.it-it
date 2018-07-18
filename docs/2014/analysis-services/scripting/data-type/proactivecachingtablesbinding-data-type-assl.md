---
title: Tipo di dati ProactiveCachingTablesBinding (ASSL) | Microsoft Docs
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
- ProactiveCachingTablesBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ProactiveCachingTablesBinding data type
ms.assetid: f6b3f6fc-757c-4b1e-bb3a-d26482888d14
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 98091714acb85771972c8c90c6b445744a33cce6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275607"
---
# <a name="proactivecachingtablesbinding-data-type-assl"></a>Tipo di dati ProactiveCachingTablesBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta le informazioni per il [ProactiveCaching](../objects/proactivecaching-element-assl.md) elemento sulle modifiche dell'origine dati in tabelle e viste che richiedono la ricompilazione della cache specificate.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ProactiveCachingTablesBinding>  
   <!-- The following elements extend ProactiveCachingObjectNotificationBinding -->  
   <TableNotification>...</TableNotification>  
</ProactiveCachingTablesBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[ProactiveCachingObjectNotificationBinding](binding-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[TableNotification](../objects/tablenotification-element-assl.md)|  
|Elementi derivati|None|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sul `ProactiveCachingBinding` tipo, inclusa una tabella della gerarchia di ereditarietà di `ProactiveCachingBinding` tipi, vedere [tipo di dati ProactiveCachingBinding &#40;ASSL&#41;](proactivecachingbinding-data-type-assl.md).  
  
 Per altre informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [associazione tipo di dati &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni di dati in ASSL, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ProactiveCachingTablesBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
