---
title: Elemento CustomRollupProperties (XMLA) | Microsoft Docs
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
- CustomRollupProperties Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.customrollupproperties
- urn:schemas-microsoft-com:xml-analysis#CustomRollupProperties
- http://schemas.microsoft.com/analysisservices/2003/engine#CustomRollupProperties
helpviewer_keywords:
- CustomRollupProperties element
ms.assetid: 4abf0129-e529-4355-b8d5-6f4e6a88e796
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a564296dd022dece7ff20a7187c2c80bba9c6b7f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37233701"
---
# <a name="customrollupproperties-element-xmla"></a>Elemento CustomRollupProperties (XMLA)
  Contiene le proprietà di rollup personalizzato per un membro dell'attributo rappresentato dall'elemento padre [attributo](attribute-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute>  
   ...  
   <CustomRollupProperties>...</CustomRollupProperties>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attribute](attribute-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `CustomRollupProperties` contiene un'espressione MDX (Multidimensional Expressions) che definisce le proprietà di rollup personalizzate del membro dell'attributo definito dall'elemento padre `Attribute`.  
  
 Per altre informazioni sulle espressioni MDX, vedere [espressioni &#40;MDX&#41;](/sql/mdx/expressions-mdx).  
  
## <a name="see-also"></a>Vedere anche  
 [Inserire l'elemento &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Aggiornare l'elemento &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
