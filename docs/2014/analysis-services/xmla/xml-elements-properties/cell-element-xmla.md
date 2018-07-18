---
title: Cella elemento (XMLA) | Microsoft Docs
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
- Cell Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cell
- http://schemas.microsoft.com/analysisservices/2003/engine#Cell
- urn:schemas-microsoft-com:xml-analysis#Cell
helpviewer_keywords:
- Cell element
ms.assetid: 88daba54-89e9-423f-8d12-8de80cf52d6b
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 18110400e76f10e9e8ac90fc2793a7a90f25d4de
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241227"
---
# <a name="cell-element-xmla"></a>Elemento Cell (XMLA)
  Contiene informazioni su una cella che deve essere aggiornata da un comando [UpdateCells](../xml-elements-commands/updatecells-element-xmla.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<UpdateCells>  
   ...  
   <Cell CellOrdinal="Long">  
      <Value>...</Value>  
   </Cell>  
   ...  
</UpdateCells>  
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
|Elementi padre|[UpdateCells](../xml-elements-commands/updatecells-element-xmla.md)|  
|Elementi figlio|[Valore](value-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|CellOrdinal|Obbligatorio `Long` attributo. Contiene la posizione ordinale in base zero della cella da aggiornare.|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sull'aggiornamento di celle, vedere [Aggiornamento di celle &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/updating-cells-xmla.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
