---
title: Elemento Return (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e8746fb9f8b397ef50b1a5c66a2132e5f0cf5c87
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968443"
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
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md), [ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Ancestor|Elementi figlio|  
|--------------|--------------------|  
|[DiscoverResponse](../../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)|[root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
|[ExecuteResponse](../../../analysis-services/xmla/xml-elements-objects-executeresponse.md)|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) o [risultati](../../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il **restituire** elemento contiene i dati restituiti dai **Discover** e **Execute** metodi. In genere, il **restituire** elemento contiene un unico **radice** elemento che contiene i dati restituiti da una **Discover** o **Execute** chiamata al metodo o un file XML per eccezione Analysis (XMLA) restituito da una chiamata di metodo non riuscita. Se il **Execute** metodo contiene un **Batch** comando che esegue più operazioni, il **restituire** elemento contiene un **risultati** elemento che, a sua volta, contiene un **radice** (elemento) per ogni comando eseguito correttamente o non correttamente dalle **Batch** comando.  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
