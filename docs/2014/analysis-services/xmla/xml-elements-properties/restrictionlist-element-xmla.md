---
title: Elemento RestrictionList (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cad57213c69c63dbc45e476d0163a46c111bc8a9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067951"
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
  
  
