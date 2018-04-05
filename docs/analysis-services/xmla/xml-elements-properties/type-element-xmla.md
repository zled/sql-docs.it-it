---
title: Tipo di elemento (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Type Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords:
- Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 363b89eddf7794174689c0d6df7805328c88eb70
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="type-element-xmla"></a>Elemento Type (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Determina il tipo di elaborazione da eseguire per il [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
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
|Elementi padre|[Process](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Osservazioni  
 Per ulteriori informazioni sulle opzioni disponibili per gli oggetti in un'istanza di elaborazione [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vedere [l'elaborazione di un modello multidimensionale &#40; Analysis Services &#41; ](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Il valore di **tipo** elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*ProcessFull*|Elimina tutti i dati dall'oggetto interessato, quindi elabora tale oggetto.|  
|*ProcessAdd*|Aggiunge nuovi dati all'oggetto interessato.|  
|*ProcessUpdate*|Aggiorna i dati nell'oggetto interessato.|  
|*ProcessIndexes*|Crea o ricompila indici e aggregazioni nell'oggetto interessato.|  
|*ProcessScriptCache*|Se il cubo viene elaborato, il server ricompila la cache script MDX. In caso contrario, viene generato un errore.<br /><br /> **Nota** si applica solo al cubo.|  
|*ProcessData*|Elabora i dati solo nell'oggetto interessato.|  
|*ProcessDefault*|Rileva lo stato dell'oggetto interessato, quindi esegue l'opzione di elaborazione appropriata sull'oggetto interessato per ottimizzarlo completamente e ripristinare uno stato dell'oggetto completamente elaborato.|  
|*ProcessClear*|Elimina i dati dall'oggetto interessato e da tutti gli oggetti correlati.|  
|*ProcessStructure*|Elabora la struttura solo dell'oggetto interessato.|  
|*ProcessClearStructureOnly*|Cancella i dati solo dall'oggetto interessato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
