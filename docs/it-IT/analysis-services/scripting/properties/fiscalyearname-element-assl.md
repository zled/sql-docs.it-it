---
title: Elemento FiscalYearName (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- FiscalYearName Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- FiscalYearName
helpviewer_keywords:
- FiscalYearName element
ms.assetid: ce613a21-6890-4796-aac5-b029eca46255
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0e9de01bb4eee1d17ce51ac35f4d869901553e0e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="fiscalyearname-element-assl"></a>Elemento FiscalYearName (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce la convenzione di denominazione per il nome dell'anno fiscale per un [TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TimeBinding>  
   ...  
   <FiscalYearName>...</FiscalYearName>  
   ...  
</TimeBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*NextCalendarYearName*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[TimeBinding](../../../analysis-services/scripting/data-type/timebinding-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*CalendarYearName*|Assegna il nome dell'anno solare corrente all'anno fiscale.|  
|*NextCalendarYearName*|Assegna il nome dell'anno solare successivo all'anno fiscale.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **FiscalYearName** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.FiscalYearName>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
