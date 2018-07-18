---
title: Elemento Folders (XMLA) | Microsoft Docs
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
- Folders Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.folders
- http://schemas.microsoft.com/analysisservices/2003/engine#Folders
- urn:schemas-microsoft-com:xml-analysis#Folders
helpviewer_keywords:
- Folders element
ms.assetid: fefb0469-22ea-4804-8dc3-9c49825b32f1
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 00d90fd45456a0b672c12cdd44706e63011cbb28
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37148532"
---
# <a name="folders-element-xmla"></a>Elemento Folders (XMLA)
  Contiene una raccolta di elementi [Folder](folder-element-xmla.md) utilizzati dall'elemento [Location](location-element-xmla.md) padre durante un comando [Restore](../xml-elements-commands/restore-element-xmla.md) o [Synchronize](../xml-elements-commands/synchronize-element-xmla.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Location>  
   ...  
   <Folders>  
      <Folder>...</Folder>  
   </Folders>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno (raccolta)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Percorso](location-element-xmla.md)|  
|Elementi figlio|[Cartella](folder-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Restore &#40;XMLA&#41;](../xml-elements-commands/restore-element-xmla.md)   
 [Elemento Synchronize &#40;XMLA&#41;](../xml-elements-commands/synchronize-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
