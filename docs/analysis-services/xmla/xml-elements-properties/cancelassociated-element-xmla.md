---
title: Elemento CancelAssociated (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
apiname: CancelAssociated Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cancelassociated
- urn:schemas-microsoft-com:xml-analysis#CancelAssociated
- http://schemas.microsoft.com/analysisservices/2003/engine#CancelAssociated
helpviewer_keywords: CancelAssociated element
ms.assetid: fd890440-d1a7-4c05-9e81-c81e6b8c274c
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 65d60344142e10f0912c81fdb7062f30b740a9ad
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="cancelassociated-element-xmla"></a>Elemento CancelAssociated (XMLA)
  Indica se l'elemento [Cancel](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) padre deve annullare tutti i comandi associati.  
  
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
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|False|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Annulla](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Se questo elemento viene specificato e impostato a **True**, ogni connessione corrispondente, sessione e comando identificati nel comando **Cancel** padre vengono annullati.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ConnectionID &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [Elemento SessionID &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [Elemento SPID &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
