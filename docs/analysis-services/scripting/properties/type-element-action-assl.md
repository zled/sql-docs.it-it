---
title: Tipo di elemento (Action) (ASSL) | Documenti Microsoft
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8b87ab109aaad0c40e1debb3a8ea84047b6e8f6b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="type-element-action-assl"></a>Elemento Type (Action) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il tipo di [azione](../../../analysis-services/scripting/objects/action-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*URL*|Visualizza una pagina variabile in un browser Internet.|  
|*HTML*|Esegue uno script HTML in un browser Internet.|  
|*Istruzione*|Esegue un comando OLE DB.|  
|*Drill-through*|Recupera un set di righe per il drill-through.<br /><br /> Questo valore è identico a *set di righe* e identifica le azioni di drill-through. Deve essere utilizzata in azioni il cui [TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md) è impostato su *celle*.|  
|*set di dati*|Consente di recuperare un set di dati.|  
|*Rowset*|Consente di recuperare un set di righe.|  
|*Riga di comando*|Esegue un comando a un prompt dei comandi.|  
|*Proprietario*|Esegue un'operazione utilizzando un'interfaccia diversa da quelle elencate in precedenza in questa tabella.|  
|*Report*|Visualizza una pagina variabile in un browser Internet.<br /><br /> Questo valore è identico a *Url* e identifica le azioni report.|  
  
 L'elemento che corrisponde all'elemento padre **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati DrillThroughAction &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)   
 [Tipo di dati ReportAction &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
