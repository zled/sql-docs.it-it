---
title: Valore elemento (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 9acc8856dfaaa250d1addc8bd1df72325a5d86c7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34039259"
---
# <a name="value-element-assl"></a>Elemento Value (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Vedere la tabella riportata di seguito.|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
|Predecessore o padre|Tipo di dati|  
|------------------------|---------------|  
|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|Any simpleType|  
|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|Any simpleType|  
|Tutti gli altri|String|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md), [annotazione](../../../analysis-services/scripting/objects/annotation-element-assl.md), [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md), [ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md), [ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md), [ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il **valore** elemento contiene il valore associato all'oggetto padre. Il valore previsto del **valore** elemento varia a seconda dell'elemento padre, come descritto nella tabella seguente.  
  
|Elemento padre|Valore previsto|  
|--------------------|--------------------|  
|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|Valore del parametro algoritmo.|  
|[Annotazione](../../../analysis-services/scripting/objects/annotation-element-assl.md)|Valore dell’annotazione.|  
|[Indicatore KPI](../../../analysis-services/scripting/objects/kpi-element-assl.md)|Un'espressione Espressioni MDX (MDX) utilizzata per calcolare il valore dell'indicatore di prestazioni chiave (Indicatore KPI).|  
|[ReportFormatParameter](../../../analysis-services/scripting/objects/reportformatparameter-element-asl.md)|Valore del parametro di formato report.|  
|[ReportParameter](../../../analysis-services/scripting/objects/reportparameter-element-assl.md)|Un'espressione MDX utilizzata per calcolare il valore del parametro del report.|  
|[ServerProperty](../../../analysis-services/scripting/objects/serverproperty-element-assl.md)|Il valore della proprietà server per l'istanza attualmente in esecuzione.|  
  
 Gli elementi che corrispondono ai padri di **valore** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.AlgorithmParameter>, <xref:Microsoft.AnalysisServices.Annotation>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.ReportParameter>, e <xref:Microsoft.AnalysisServices.ServerProperty>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
