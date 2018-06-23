---
title: Elemento CalendarStartDate (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- CalendarStartDate Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CalendarStartDate
helpviewer_keywords:
- CalendarStartDate element
ms.assetid: f6204107-9123-41f0-acbd-52134fe36e37
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 9e0fd15c7fa6336c1fb1ea245eb400079e95e76d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065226"
---
# <a name="calendarstartdate-element-assl"></a>Elemento CalendarStartDate (ASSL)
  Definisce la data di inizio del periodo di calendario per la [TimeBinding](../data-type/binding-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TimeBinding>  
   ...  
   <CalendarStartDate>...</CalendarStartDate>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|DateTime|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[TimeBinding](../data-type/binding-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 `CalendarEndDate` deve cadere dopo `CalendarStartDate`.  
  
 L'elemento che corrisponde al padre di `CalendarStartDate` nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  