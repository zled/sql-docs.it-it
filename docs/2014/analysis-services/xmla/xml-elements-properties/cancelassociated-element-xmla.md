---
title: Elemento CancelAssociated (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CancelAssociated Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cancelassociated
- urn:schemas-microsoft-com:xml-analysis#CancelAssociated
- http://schemas.microsoft.com/analysisservices/2003/engine#CancelAssociated
helpviewer_keywords:
- CancelAssociated element
ms.assetid: fd890440-d1a7-4c05-9e81-c81e6b8c274c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 294f1060c0a52c357e791d5b3db7ad87d0d98309
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126591"
---
# <a name="cancelassociated-element-xmla"></a>Elemento CancelAssociated (XMLA)
  Indica se l'elemento [Cancel](../xml-elements-commands/cancel-element-xmla.md) padre deve annullare tutti i comandi associati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cancel>  
   ...  
   <ConnectionID>...</ConnectionID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|False|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Annulla](../xml-elements-commands/cancel-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Se questo elemento viene specificato e impostato su `True`, ogni connessione corrispondente, sessione e comando identificati nel padre `Cancel` viene annullato.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ConnectionID &#40;XMLA&#41;](id-element-xmla.md)   
 [Elemento SessionID &#40;XMLA&#41;](sessionid-element-xmla.md)   
 [Elemento SPID &#40;XMLA&#41;](spid-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
