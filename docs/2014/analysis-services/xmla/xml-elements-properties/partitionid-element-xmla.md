---
title: Elemento PartitionID (XMLA) | Microsoft Docs
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
- PartitionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#PartitionID
- urn:schemas-microsoft-com:xml-analysis#PartitionID
- microsoft.xml.analysis.partitionid
helpviewer_keywords:
- PartitionID element
ms.assetid: 19f06454-9719-488e-aeb6-3fc879313351
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 663d1723598354cf4ea762ee51d34921feb516c7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37231831"
---
# <a name="partitionid-element-xmla"></a>Elemento PartitionID (XMLA)
  Identifica una partizione all'interno di un elemento padre che contiene un riferimento a un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Object> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <PartitionID>...</PartitionID>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|Se predecessore o padre =<br />                        [Source](source-element-xmla.md), [Target](../xml-elements-properties/target-element-xmla.md)<br /><br /> Cardinalità = 1-1: elemento obbligatorio che ricorre una sola volta.<br /><br /> Se predecessore o padre = tutti gli altri:<br /><br /> Cardinalità = 0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Object](object-element-xmla.md), [ParentObject](parentobject-element-xmla.md), [Source](source-element-xmla.md), [Target](../xml-elements-properties/target-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
