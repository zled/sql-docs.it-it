---
title: Valore elemento (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Value Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Value
helpviewer_keywords:
- Value element
ms.assetid: a2fad411-73fd-42df-b4e1-df2cb8454182
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d338b8607d8515bf89183eeadd24252c55af8fc5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218191"
---
# <a name="value-element-assl"></a>Elemento Value (ASSL)
  Contiene il valore dell'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AlgorithmParameter> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Value>...</Value>  
   ...  
</AlgorithmParameter>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
|Predecessore o padre|Tipo di dati|  
|------------------------|---------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|Any simpleType|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|Any simpleType|  
|Tutti gli altri|String|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md), [annotazione](../objects/annotation-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [ReportFormatParameter](../objects/reportformatparameter-element-asl.md), [ReportParameter](../objects/reportparameter-element-assl.md), [ServerProperty](../objects/serverproperty-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L’elemento `Value` contiene il valore associato all'oggetto padre. Il valore previsto dell'elemento `Value` varia a seconda dell'elemento padre, come descritto nella tabella seguente.  
  
|Elemento padre|Valore previsto|  
|--------------------|--------------------|  
|[AlgorithmParameter](../objects/algorithmparameter-element-assl.md)|Valore del parametro algoritmo.|  
|[Annotazione](../objects/annotation-element-assl.md)|Valore dell’annotazione.|  
|[Indicatore KPI](../objects/kpi-element-assl.md)|Un'espressione Espressioni MDX (MDX) utilizzata per calcolare il valore dell'indicatore di prestazioni chiave (Indicatore KPI).|  
|[ReportFormatParameter](../objects/reportformatparameter-element-asl.md)|Valore del parametro di formato report.|  
|[ReportParameter](../objects/reportparameter-element-assl.md)|Un'espressione MDX utilizzata per calcolare il valore del parametro del report.|  
|[ServerProperty](../objects/serverproperty-element-assl.md)|Il valore della proprietà server per l'istanza attualmente in esecuzione.|  
  
 Gli elementi che corrispondono agli elementi padre di `Value` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.AlgorithmParameter>, <xref:Microsoft.AnalysisServices.Annotation>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.ReportParameter> e <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
