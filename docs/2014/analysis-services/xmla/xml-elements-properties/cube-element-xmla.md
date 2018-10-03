---
title: Elemento (XMLA) del cubo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Cube Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.cube
- urn:schemas-microsoft-com:xml-analysis#Cube
- http://schemas.microsoft.com/analysisservices/2003/engine#Cube
helpviewer_keywords:
- Cube element
ms.assetid: 2e8662f4-fb2e-43af-b70a-9e0b5872c9b9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: de5c375e5e517e155bd6efb4beeeef61e9f31a79
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48103361"
---
# <a name="cube-element-xmla"></a>Elemento Cube (XMLA)
  Identifica il cubo che contiene la dimensione rappresentata dall'elemento padre [oggetto](object-element-dimension-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Object>  
   ...  
   <Cube>...</Cube>  
   ...  
</Object>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Oggetto](object-element-dimension-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `Cube` è un identificatore di oggetto contenente il nome del cubo che contiene la dimensione rappresentata dall'elemento `Object`.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento database &#40;XMLA&#41;](database-element-xmla.md)   
 [Elemento della dimensione &#40;XMLA&#41;](dimension-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
