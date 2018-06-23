---
title: Tipo di dati TimeBinding (ASSL) | Documenti Microsoft
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
- TimeBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TimeBinding
helpviewer_keywords:
- TimeBinding data type
ms.assetid: f3c06978-c181-4a73-9b57-8fc30358faab
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 80fe87cf9bc54fa97f0ffe56d8f2105bb6381e28
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066778"
---
# <a name="timebinding-data-type-assl"></a>Tipo di dati TimeBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta un'associazione a periodi di tempo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TimeBinding>  
   <!-- The following elements extend Binding -->  
      <CalendarStartDate>...</CalendarStartDate>  
      <CalendarEndDate>...</CalendarEndDate>  
      <FirstDayOfWeek>...</FirstDayOfWeek>  
   <CalendarLanguage>...</CalendarLanguage>  
   <FiscalFirstMonth>...</FiscalFirstMonth>  
   <FiscalFirstDayOfMonth>...</FiscalFirstDayOfMonth>  
   <FiscalYearName>...</FiscalYearName>  
   <ReportingFirstMonth>...</ReportingFirstMonth>  
   <ReportingFirstWeekOfMonth>...</ReportingFirstWeekOfMonth>  
   <ReportingWeekToMonthPattern>...</ReportingWeekToMonthPattern>  
   <ManufacturingFirstMonth>...</ManufacturingFirstMonth>  
   <ManufacturingFirstWeekOfMonth>...</ManufacturingFirstWeekOfMonth>  
   <ManufacturingExtraMonthQuarter>...</ManufacturingExtraMonthQuarter>  
</TimeBinding>  
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
|Elementi figlio|[CalendarEndDate](../properties/calendarenddate-element-assl.md), [CalendarLanguage](../properties/language-element-assl.md), [CalendarStartDate](../properties/calendarstartdate-element-assl.md), [FirstDayOfWeek](../properties/firstdayofweek-element-assl.md), [FiscalFirstDayOfMonth](../properties/fiscalfirstdayofmonth-element-assl.md), [FiscalFirstMonth](../properties/fiscalfirstmonth-element-assl.md), [FiscalYearName](../properties/name-element-assl.md), [ManufacturingExtraMonthQuarter](../properties/manufacturingextramonthquarter-element-assl.md), [ManufacturingFirstMonth](../properties/manufacturingfirstmonth-element-assl.md), [ManufacturingFirstWeekOfMonth](../properties/manufacturingfirstweekofmonth-element-assl.md), [ReportingFirstMonth](../properties/reportingfirstmonth-element-assl.md), [ReportingFirstWeekOfMonth](../properties/reportingfirstweekofmonth-element-assl.md), [ReportingWeekToMonthPattern](../properties/reportingweektomonthpattern-element-assl.md)|  
|Elementi derivati|Vedere [associazione](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Remarks  
 Per ulteriori informazioni sul `Binding` tipo, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) del `Binding` tipo e la gerarchia di ereditarietà dei `Binding` tipi, vedere [associazione tipo di dati &#40;ASSL &#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni dati in ASSL, vedere [origini dati e le associazioni &#40;multidimensionali SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.TimeBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  