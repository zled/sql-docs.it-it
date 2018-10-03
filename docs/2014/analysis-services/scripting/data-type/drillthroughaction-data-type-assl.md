---
title: Tipo di dati DrillThroughAction (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DrillThroughAction Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DrillThroughAction
helpviewer_keywords:
- DrillThroughAction data type
ms.assetid: e212d575-a0d7-4548-92b4-33542ef59034
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e6a1ccdedbcb1b70e9673afe687a62f95065c3aa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219391"
---
# <a name="drillthroughaction-data-type-assl"></a>Tipo di dati DrillThroughAction (ASSL)
  Definisce un tipo di dati derivato che rappresenta un'azione drill-through.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DrillThroughAction>  
   <!-- The following elements extend Action -->  
   <Default>...</Default>  
   <Columns>...</Columns>  
</DrillThroughAction>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Azione](action-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Le colonne](../collections/columns-element-assl.md), [predefinito](../properties/default-element-assl.md)|  
|Elementi derivati|[Azione](../objects/action-element-assl.md) ([azioni](../collections/actions-element-assl.md), raccolta di [cubo](../objects/cube-element-assl.md), oppure [prospettiva](../objects/perspective-element-assl.md))|  
  
## <a name="remarks"></a>Note  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DrillThroughAction>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
