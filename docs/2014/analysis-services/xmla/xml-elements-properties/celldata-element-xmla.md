---
title: Elemento CellData (XMLA) | Microsoft Docs
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
- CellData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CellData
- http://schemas.microsoft.com/analysisservices/2003/engine#CellData
- urn:schemas-microsoft-com:xml-analysis#CellData
- microsoft.xml.analysis.celldata
helpviewer_keywords:
- CellData element
ms.assetid: 0ebfb5e1-a674-4b9b-bd8c-c529da105f61
caps.latest.revision: 27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 370837c78fe1fa49396a5209dd94dd0e7cb4f69d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330411"
---
# <a name="celldata-element-xmla"></a>Elemento CellData (XMLA)
  Contiene una raccolta di elementi Cell che rappresentano i dati delle celle contenuti in un [radice](root-element-xmla.md) elemento che utilizza il [MDDataSet](../xml-data-types/mddataset-data-type-xmla.md) tipo di dati.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:mddataset">  
   ...  
   <CellData>  
      <Cell>...</Cell>  
   </CellData>  
</root>  
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
|Elementi padre|[root](root-element-xmla.md)|  
|Elementi figlio|[Cella](cell-element-mddataset-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Nell'elemento radice padre l'elemento `Axes` è seguito dall'elemento `CellData`, una raccolta di elementi `Cell` che contengono i valori di proprietà di cella per ogni cella restituita nel dataset multidimensionale.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
