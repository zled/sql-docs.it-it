---
title: Elemento Language (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4b2e3a188a9681508473394a6323457cc4fa1726
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036829"
---
# <a name="language-element-xmla"></a>Elemento Language (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene l'identificatore delle impostazioni locali (LCID) per l'elemento padre [traduzione](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Translation>  
   ...  
   <Language>...</Language>  
   ...  
</Translation>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Valore intero|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Traduzione](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il **Language** elemento specifica l'identificatore LCID utilizzato dall'elemento padre **traduzione** elemento a cui assegnare il **Name** dell'elemento padre **traduzione** elemento a un membro dell'attributo, per la lingua specificata, durante un' **inserire** oppure **Update** comando.  
  
## <a name="see-also"></a>Vedere anche
 [Inserire l'elemento &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Denominare l'elemento &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/name-element-xmla.md)   
 [Aggiornare l'elemento &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
