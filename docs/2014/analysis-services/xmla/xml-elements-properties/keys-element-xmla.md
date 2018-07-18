---
title: Tasti di elemento (XMLA) | Microsoft Docs
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
- Keys Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Keys
- http://schemas.microsoft.com/analysisservices/2003/engine#Keys
- microsoft.xml.analysis.keys
helpviewer_keywords:
- Keys element
ms.assetid: 67291791-0032-412a-9a4f-74f68533e83d
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6875795b79daa2be3942f0e9e71ab6c4d2e6c960
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310381"
---
# <a name="keys-element-xmla"></a>Elemento Keys (XMLA)
  Contiene una raccolta di [Key](key-element-xmla.md) gli elementi utilizzati per identificare le chiavi del membro dell'attributo rappresentato dall'elemento padre [attributo](attribute-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute>  
   ...  
   <Keys>  
      <Key>...</Key>  
   </Keys>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attribute](attribute-element-xmla.md)|  
|Elementi figlio|[Key](key-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DROP &#40;XMLA&#41;](../xml-elements-commands/drop-element-xmla.md)   
 [Inserire l'elemento &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Aggiornare l'elemento &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
