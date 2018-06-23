---
title: Chiave elemento (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Key Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Key
- urn:schemas-microsoft-com:xml-analysis#Key
- microsoft.xml.analysis.key
helpviewer_keywords:
- Key element
ms.assetid: 09d3cd48-49f7-4b58-b8bb-ca75b81bb02f
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: d6ec30e8c55648975294f82a7c927b3815b00471
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055076"
---
# <a name="key-element-xmla"></a>Elemento Key (XMLA)
  Contiene un valore di chiave membro per un membro dell'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Keys>  
   ...  
   <Key>...</Key>  
   ...  
</Keys>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Qualsiasi|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Chiavi](keys-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il tipo di dati utilizzato da questo elemento deve corrispondere al tipo di dati della colonna chiave appropriata dell'attributo specificato. Se gli elementi `Key` non sono specificati per un elemento padre `Attribute`, gli elementi `AttributeName` e `Name` specificati nell'elemento padre `Attribute` vengono utilizzati per identificare il membro dell'attributo da modificare.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento dell'attributo &#40;XMLA&#41;](attribute-element-xmla.md)   
 [Elemento AttributeName &#40;XMLA&#41;](name-element-xmla.md)   
 [Elemento DROP &#40;XMLA&#41;](../xml-elements-commands/drop-element-xmla.md)   
 [Inserire l'elemento &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Elemento KeyColumn &#40;ASSL&#41;](../../scripting/objects/column-element-assl.md)   
 [Aggiornare l'elemento &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [In cui elemento &#40;XMLA&#41;](where-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  