---
title: Elemento FolderPosition (XML) | Microsoft Docs
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
ms.assetid: 8cccef2b-bdd0-415a-bb53-bda14165d1e4
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a55c84438516e99d9eac86db498fa4a5102d9d0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219891"
---
# <a name="folderposition-element-xml"></a>Elemento FolderPosition (XML)
  Contiene informazioni sulla posizione dell'elemento in una raccolta di elementi.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <FolderPosition>...</FolderPosition>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Valore intero|  
|Valore predefinito|-1|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per gli elementi `RelationshipEndVisualizationProperties`, l'elemento `FolderPosition` contiene la posizione dell'elemento cartella predefinita in una raccolta di cartelle. Il valore predefinito di `false` indica che non è presente alcuna cartella predefinita da utilizzare.  
  
  
