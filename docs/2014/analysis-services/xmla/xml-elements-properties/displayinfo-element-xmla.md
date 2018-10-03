---
title: Elemento DisplayInfo (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DisplayInfo Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.displayinfo
- http://schemas.microsoft.com/analysisservices/2003/engine#DisplayInfo
- urn:schemas-microsoft-com:xml-analysis#DisplayInfo
helpviewer_keywords:
- DisplayInfo element
ms.assetid: 059ce038-38de-4c7d-a72f-4f919cfc7c4a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e3ff6bf5ad29ffff059752d97b03f778c5edbcf7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48101651"
---
# <a name="displayinfo-element-xmla"></a>Elemento DisplayInfo (XMLA)
  Contiene informazioni di visualizzazione per l'elemento padre [HierarchyInfo](hierarchyinfo-element-xmla.md) oppure [membro](member-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <DisplayInfo>...</DisplayInfo>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|unsignedInt|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[HierarchyInfo](hierarchyinfo-element-xmla.md), [membro](member-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 L'elemento `DisplayInfo` contiene vari elementi di informazioni che aiutano un'applicazione client a eseguire il rendering dell'elemento padre `HierarchyInfo` o `Member`. Il valore è equivalente alla proprietà DISPLAY_INFO definita per i set di righe dell'asse nella specifica OLE DB per OLAP.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
