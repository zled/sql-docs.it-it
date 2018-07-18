---
title: Elemento SPID (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 39f4391ef919ad3de5233df078535b34691e1424
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036689"
---
# <a name="spid-element-xmla"></a>Elemento SPID (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Identifica un identificatore di processo active server (SPID) in cui eseguire l'elemento padre [annullare](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cancel>  
   ...  
   <SPID>...</SPID>  
   ...  
</Cancel>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Valore intero|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Annulla](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il **SPID** elemento rappresenta il processo server ID (SPID) usato per una determinata sessione in un'istanza di Analysis Services.  
  
## <a name="see-also"></a>Vedere anche
 [Elemento CancelAssociated &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md)   
 [Elemento ConnectionID &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md)   
 [Elemento SessionID &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
