---
title: Elemento IsDefaultMeasure (XML) | Microsoft Docs
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
ms.assetid: 523cf3d7-9df0-4f9d-8486-9109de8d3cca
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c89445c0e31187951b4b4a9f2bbd6f97733e9572
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37190851"
---
# <a name="isdefaultmeasure-element-xml"></a>Elemento IsDefaultMeasure (XML)
  Indica che è possibile ottenere la misura predefinita per questa entità spostando questa relazione all'altra tabella e recuperando il membro con l'attributo DefaultMeasure.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<RelationshipEndVisualizationProperties>  
   ...  
   <IsDefaultMeasure>...</IsDefaultMeasure>  
   ...  
</RelationshipEndVisualizationProperties>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|false|  
|Cardinalità|0-1: elemento facoltativo che ricorre una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[RelationshipEndVisualizationProperties](../../scripting/data-type/relationshipendvisualizationproperties-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per gli elementi `RelationshipEndVisualizationProperties` l'elemento `IsDefaultMeasure` indica che è possibile ottenere la misura predefinita per questa entità spostandosi sull'altra estremità di questa relazione. Il valore predefinito di `false` indica che non è presente alcuna misura predefinita da ottenere.  
  
  
