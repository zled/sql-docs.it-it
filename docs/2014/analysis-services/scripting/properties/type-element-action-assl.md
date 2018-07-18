---
title: Tipo di elemento (Action) (ASSL) | Microsoft Docs
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
- Type Element (Action)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 99147acb4b2a1b467913087f4e4df14469de9a03
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249082"
---
# <a name="type-element-action-assl"></a>Elemento Type (Action) (ASSL)
  Contiene il tipo dei [azione](../objects/action-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Azione](../objects/action-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*URL*|Visualizza una pagina variabile in un browser Internet.|  
|*HTML*|Esegue uno script HTML in un browser Internet.|  
|*Istruzione*|Esegue un comando OLE DB.|  
|*Drill-through*|Recupera un set di righe per il drill-through.<br /><br /> Questo valore è identico a *set di righe* e identifica le azioni di drill-through. Può solo essere usata in azioni il cui [TargetType](targettype-element-assl.md) è impostato su *celle*.|  
|*Set di dati*|Consente di recuperare un set di dati.|  
|*Rowset*|Consente di recuperare un set di righe.|  
|*Riga di comando*|Esegue un comando a un prompt dei comandi.|  
|*Proprietario*|Esegue un'operazione utilizzando un'interfaccia diversa da quelle elencate in precedenza in questa tabella.|  
|*Report*|Visualizza una pagina variabile in un browser Internet.<br /><br /> Questo valore è identico a *Url* e identifica le azioni report.|  
  
 L'elemento che corrisponde al padre di `Type` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.Action>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati DrillThroughAction &#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [Tipo di dati ReportAction &#40;ASSL&#41;](../data-type/reportaction-data-type-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
