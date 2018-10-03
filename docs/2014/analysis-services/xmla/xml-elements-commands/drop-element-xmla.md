---
title: Elemento DROP (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Drop Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Drop
- microsoft.xml.analysis.drop
- http://schemas.microsoft.com/analysisservices/2003/engine#Drop
helpviewer_keywords:
- Drop element
ms.assetid: a5d21db3-743a-4958-b16d-b6816a5ee787
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b723e6ae10ae045ce43c7138ce481ffdab3955bd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194941"
---
# <a name="drop-element-xmla"></a>Elemento Drop (XMLA)
  Elimina membri dell'attributo da una dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Drop>  
      <Object>...</Object>  
      <DeleteWithDescendants>...</DeleteWithDescendants>  
      <Where>...</Where>  
   </Drop>  
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
|Elementi figlio|[DeleteWithDescendants](../xml-elements-properties/deletewithdescendants-element-xmla.md), [oggetto](../xml-elements-properties/object-element-dimension-xmla.md), [dove](../xml-elements-properties/where-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Il comando `Drop` elimina membri dell'attributo da una dimensione abilitata alla scrittura.  
  
 Per altre informazioni sull'eliminazione di membri, vedere [inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Inserire l'elemento &#40;XMLA&#41;](insert-element-xmla.md)   
 [Aggiornare l'elemento &#40;XMLA&#41;](update-element-xmla.md)   
 [I comandi &#40;XMLA&#41;](xml-elements-commands.md)  
  
  
