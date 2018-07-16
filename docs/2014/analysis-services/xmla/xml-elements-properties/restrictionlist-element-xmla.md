---
title: Elemento RestrictionList (XMLA) | Microsoft Docs
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
- RestrictionList Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#RestrictionList
- microsoft.xml.analysis.restrictionlist
- http://schemas.microsoft.com/analysisservices/2003/engine#RestrictionList
helpviewer_keywords:
- RestrictionList element
ms.assetid: 2297c005-381e-49a4-a207-826f7f9ea93a
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 045c5644608c7f9537124450ef2c5637eebbb796
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314591"
---
# <a name="restrictionlist-element-xmla"></a>Elemento RestrictionList (XMLA)
  Contiene una raccolta di colonne e dati di restrizione utilizzati dal metodo [Discover](../xml-elements-methods-discover.md) .  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Restrictions>  
   <RestrictionList>  
      <!-- Zero or more restriction columns and values -->  
   </RestrictionList>  
</Restrictions>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Restrizioni](restrictions-element-xmla.md)|  
|Elementi figlio|Colonne e valori di restrizione (vedere la sezione Commenti).|  
  
## <a name="remarks"></a>Note  
 L'elemento `RestrictionList` contiene una raccolta di colonne di restrizione in base alla quale è possibile filtrare i dati restituiti dal metodo `Discover`. Ogni colonna di restrizione nell'elemento `RestrictionList` è definita da un elemento XML distinto. Il valore della colonna di restrizione corrisponde ai dati contenuti nell'elemento XML, mentre il nome della colonna di restrizione corrisponde al nome dell'elemento XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
