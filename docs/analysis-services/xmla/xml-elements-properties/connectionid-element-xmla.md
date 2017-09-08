---
title: Elemento ConnectionID (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ConnectionID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ConnectionID
- http://schemas.microsoft.com/analysisservices/2003/engine#ConnectionID
- microsoft.xml.analysis.connectionid
helpviewer_keywords:
- ConnectionID element
ms.assetid: de044fb2-f713-46b2-8899-14e8d515e823
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 246ac054d937ce49e0f758705ea929f4159a8ccf
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="connectionid-element-xmla"></a>Elemento ConnectionID (XMLA)
  Identifica una connessione attiva in cui eseguire l'elemento padre [Annulla](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cancel>  
   ...  
   <ConnectionID>...</ConnectionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Valore intero|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Annulla](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento CancelAssociated &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Elemento SessionID &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [Elemento SPID &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
