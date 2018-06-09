---
title: Elemento (XMLA) dei messaggi | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 29780b5578c5e48c2ff8781719f9ebffe065e62c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575703"
---
# <a name="message-element-xmla"></a>Elemento Message (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene un messaggio restituito da un'istanza di Analysis Services da un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) oppure [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Messages>  
   ...  
   <Message>  
      <Error>...</Error>  
      <!-- or -->  
      <Warning>...</Warning>  
   </Message>  
   ...  
</Messages>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Messaggi](../../../analysis-services/xmla/xml-elements-properties/messages-element-xmla.md)|  
|Elementi figlio|[Errore](../../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md), [avviso](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Questo elemento viene utilizzato nei casi in cui una chiamata al metodo **Discover** o un singolo comando XMLA all'interno di una chiamata al metodo **Execute** viene completato correttamente, ma con errori o avvisi. In questi casi, un **messaggi** elemento viene aggiunto all'elemento radice dopo tutti gli altri elementi, che a sua volta contiene uno o più **messaggio** elementi. Ogni **messaggio** elemento rappresenta un singolo messaggio, un errore o avviso, restituito dal [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
