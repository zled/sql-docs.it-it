---
title: Tipo di elemento (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a080a1af46df731befc8ab66ce925b961be9b16
ms.sourcegitcommit: cfe5b2af733e7801558b441b4b9427cfe4c26435
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2018
ms.locfileid: "34576713"
---
# <a name="type-element-xmla"></a>Elemento Type (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Determina il tipo di elaborazione da eseguire per il [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) elemento.  
  
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
  
## <a name="remarks"></a>Remarks  
 Per ulteriori informazioni sulle opzioni di elaborazione disponibili per gli oggetti in un'istanza di Analysis Services, vedere [l'elaborazione di un modello multidimensionale &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
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
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
