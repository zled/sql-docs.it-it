---
title: Elemento Return (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6d6130d367f38a9f2ca04d2ae3ac26c9bcb93c9b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="return-element-xmla"></a>Elemento return (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene informazioni restituite da una [DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md) elemento in risposta a un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) chiamata al metodo o un [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md) elemento in risposta a un [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) chiamata al metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DiscoverResponse> <!-- or ExecuteResponse -->  
   <return>  
      <root>...</root>  
      <!-- or -->  
      <results>...</results> <!-- ExecuteResponse only -->  
   </return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md), [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Ancestor|Elementi figlio|  
|--------------|--------------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) o [risultati](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **restituire** elemento contiene i dati restituiti dal **Discover** e **Execute** metodi. In genere, il **restituire** elemento contiene un singolo **radice** elemento che contiene i dati restituiti da una **Discover** o **Execute** chiamata al metodo o un file XML per l'eccezione Analysis (XMLA) restituita da una chiamata al metodo non riuscito. Se il **Execute** metodo contiene un **Batch** comando che vengono eseguite più operazioni, il **restituire** elemento contiene un **risultati** elemento che, a sua volta, contiene un **radice** elemento per ogni comando eseguito da esito positivo o negativo di **Batch** comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
