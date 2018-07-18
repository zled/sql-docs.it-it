---
title: Tipo di dati AggregationInstanceAttribute (ASSL) | Microsoft Docs
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
- AggregationInstanceAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- AggregationInstanceAttribute data type
ms.assetid: fc5a98bf-7c3c-4faf-b9f8-16eb073d7dc7
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8865c55a994cfb698ceea019998fe0e44e65c33b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297331"
---
# <a name="aggregationinstanceattribute-data-type-assl"></a>Tipo di dati AggregationInstanceAttribute (ASSL)
  Definisce un tipo di dati primitivo che rappresenta le informazioni su un attributo utilizzato da un'istanza di aggregazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationInstanceAttribute>  
   <AttributeID>...</AttributeID>  
   <KeyColumns>...</KeyColumns>  
</AggregationInstanceAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Elemento AttributeID](../properties/id-element-assl.md), [KeyColumns](../collections/columns-element-assl.md)|  
|Elementi derivati|[Attribute](../objects/attribute-element-assl.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
