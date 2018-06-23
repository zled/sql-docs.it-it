---
title: Tipo di dati AttributeBinding (ASSL) | Documenti Microsoft
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
- AttributeBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeBinding
helpviewer_keywords:
- AttributeBinding data type
ms.assetid: 24d511a9-d0eb-4150-9f78-541e03963d67
caps.latest.revision: 44
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 796e20c3047914ca65e7d48be26fbc951695e583
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065930"
---
# <a name="attributebinding-data-type-assl"></a>Tipo di dati AttributeBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta un'associazione per un [attributo](../objects/attribute-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeBinding>  
   <AttributeID>...</AttributeID>  
      <Type>...</Type>  
   <Ordinal>...</Ordinal>  
</AttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Associazione](binding-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Oggetto AttributeID](../properties/id-element-assl.md), [ordinale](../properties/ordinal-element-assl.md), [tipo](../properties/type-element-binding-assl.md)|  
|Elementi derivati|Vedere [associazione](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Per ulteriori informazioni sul `Binding` tipo di dati, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) derivati dal `Binding` del tipo di dati, vedere [associazione tipo di dati &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e le associazioni &#40;multidimensionali SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AttributeBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  