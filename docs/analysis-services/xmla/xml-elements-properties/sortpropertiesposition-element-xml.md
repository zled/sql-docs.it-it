---
title: Elemento SortPropertiesPosition (XML) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 68b040a7-ab16-46f5-8610-21db07df9181
caps.latest.revision: 6
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b4579aa9873c23ad3490763ce5c5900dcc8158aa
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="sortpropertiesposition-element-xml"></a>Elemento SortPropertiesPosition (XML)
  Contiene informazioni sulla posizione dell'elemento in una raccolta di elementi.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <SortPropertiesPosition>...</SortPropertiesPosition>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Valore intero|  
|Valore predefinito|-1|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[RelationshipEndVisualizationProperties](../../../analysis-services/scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per **RelationshipEndVisualizationProperties** elementi, il **SortPropertiesPosition** elemento contiene la posizione dell'elemento di proprietà di ordinamento in una raccolta di dettagli. Il valore predefinito indica che non sono presenti proprietà di ordinamento da utilizzare.  
  
  

