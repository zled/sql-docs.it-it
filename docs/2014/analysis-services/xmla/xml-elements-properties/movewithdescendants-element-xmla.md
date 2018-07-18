---
title: Elemento MoveWithDescendants (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MoveWithDescendants Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.movewithdescendants
- http://schemas.microsoft.com/analysisservices/2003/engine#MoveWithDescendants
- urn:schemas-microsoft-com:xml-analysis#MoveWithDescendants
helpviewer_keywords:
- MoveWithDescendants element
ms.assetid: d02285b6-1801-4da9-8e2b-9ab008e25558
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b75fffd4d923b7593f403ae2268b980a5ab6de6f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332571"
---
# <a name="movewithdescendants-element-xmla"></a>Elemento MoveWithDescendants (XMLA)
  Indica se i discendenti di membri dell'attributo vengono aggiornati anche dall'elemento padre [Update](../xml-elements-commands/update-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Update>  
   ...  
   <MoveWithDescendants>...</MoveWithDescendants>  
   ...  
</Update>  
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
|Elementi padre|[Update](../xml-elements-commands/update-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il `MoveWithDescendants` elemento determina se il `Update` comando non deve aggiornare solo i membri dell'attributo identificati dalle [attributi](attributes-element-xmla.md) elemento, ma anche che i discendenti di quei membri dell'attributo devono essere anch'esso aggiornato.  
  
> [!NOTE]  
>  Questo elemento si applica solo a membri attributo nelle gerarchie padre-figlio.  
  
 Per altre informazioni sull'aggiornamento di membri, vedere [inserimento, aggiornamento ed eliminazione di membri &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/inserting-updating-and-dropping-members-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
