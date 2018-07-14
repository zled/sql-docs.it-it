---
title: Elemento CommonIdentifierPosition (XML) | Microsoft Docs
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
ms.assetid: c3b64132-3b2e-46f5-ae11-a3cb3c42099c
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7d648b09d5fa005a290150a8aef91b89a328938b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267067"
---
# <a name="commonidentifierposition-element-xml"></a>Elemento CommonIdentifierPosition (XML)
  Contiene informazioni sulla posizione dell'elemento in una raccolta di elementi.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <CommonIdentifierPosition>...</CommonIdentifierPosition>  
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
 Per gli elementi `RelationshipEndVisualizationProperties`, l'elemento `CommonIdentifierPosition` contiene la posizione dell'elemento identificatore comune in una raccolta di dettagli. Il valore predefinito di `false` indica che non è presente alcun identificatore comune da utilizzare.  
  
  
