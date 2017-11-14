---
title: Elemento Return (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- return Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 06b93a7d4c785f8e298a40d6b0accd2ad945b53e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="return-element-xmla"></a>Elemento return (XMLA)
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
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

