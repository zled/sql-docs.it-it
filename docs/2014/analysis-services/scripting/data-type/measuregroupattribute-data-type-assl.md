---
title: Tipo di dati MeasureGroupAttribute (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MeasureGroupAttribute Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MeasureGroupAttribute
helpviewer_keywords:
- MeasureGroupAttribute data type
ms.assetid: dc7f71e6-3755-4d99-9fcd-5830e10eb653
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 996fdfbec8996d925c67f55f4dd6ad3cf423d0b6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177807"
---
# <a name="measuregroupattribute-data-type-assl"></a>Tipo di dati MeasureGroupAttribute (ASSL)
  Definisce un tipo di dati primitivo che rappresenta la relazione tra un attributo e un gruppo di misure.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroupAttribute>  
   <AttributeID>...</AttributeID>  
      <KeyColumns>...</KeyColumns>  
   <Type>...</Type>  
   <Annotations>...</Annotations>  
</MeasureGroupAttribute>  
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
|Elementi figlio|[Le annotazioni](../collections/annotations-element-assl.md), [AttributeID](../properties/id-element-assl.md), [KeyColumns](../collections/columns-element-assl.md), [tipo](../properties/type-element-measuregroupattribute-assl.md)|  
|Elementi derivati|[Attributo](../objects/attribute-element-assl.md) ([attributi](../collections/attributes-element-assl.md) insieme [RegularMeasureGroupDimension](dimension-data-type-assl.md))|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
