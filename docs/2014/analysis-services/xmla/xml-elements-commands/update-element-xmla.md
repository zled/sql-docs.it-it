---
title: Elemento Update (XMLA) | Microsoft Docs
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
- Update Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Update
- microsoft.xml.analysis.update
- http://schemas.microsoft.com/analysisservices/2003/engine#Update
helpviewer_keywords:
- Update command [XMLA]
ms.assetid: 324dcc16-865d-4d0a-b393-2b06c18ac807
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 75dda4a163ce6551246e11aa9eba6b57fcd9fb25
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283957"
---
# <a name="update-element-xmla"></a>Elemento Update (XMLA)
  Aggiorna i membri attributo in una dimensione  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Update>  
      <Object>...</Object>  
      <MoveWithDescendants>...</MoveWithDescendants>  
      <Attributes>...</Attributes>  
      <Where>...</Where>  
   </Update>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|[Gli attributi](../xml-elements-properties/attributes-element-xmla.md), [MoveWithDescendants](../xml-elements-properties/movewithdescendants-element-xmla.md), [oggetto](../xml-elements-properties/object-element-dimension-xmla.md), [dove](../xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il comando `Update` sposta membri dell'attributo all'interno di una dimensione abilitata per la scrittura.  
  
 Per altre informazioni sull'aggiornamento di membri, vedere [inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DROP &#40;XMLA&#41;](drop-element-xmla.md)   
 [Inserire l'elemento &#40;XMLA&#41;](insert-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
