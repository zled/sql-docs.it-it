---
title: Didascalia elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Caption Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Caption
- http://schemas.microsoft.com/analysisservices/2003/engine#Caption
- microsoft.xml.analysis.caption
helpviewer_keywords:
- Caption element
ms.assetid: 3d10ee68-98ab-4da0-a409-800dea2f1c32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4899f19b8a3986e2063d2979ce84c0a0d52d0d02
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201481"
---
# <a name="caption-element-xmla"></a>Elemento Caption (XMLA)
  Contiene informazioni sulla didascalia dell'elemento padre [HierarchyInfo](hierarchyinfo-element-xmla.md) oppure [membro](member-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <Caption>...</Caption>  
   ...  
</HierarchyInfo>  
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
|Elementi padre|[HierarchyInfo](hierarchyinfo-element-xmla.md), [membro](member-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per gli elementi `HierarchyInfo`, l'elemento `Caption` contiene il nome della proprietà che fornisce le didascalie del membro della gerarchia. Il valore è equivalente alla proprietà MEMBER_CAPTION definita per i set di righe dell'asse nella specifica OLE DB per OLAP.  
  
 Per gli elementi `Member`, l'elemento `Caption` contiene la didascalia dell'elemento padre `Member` nel linguaggio specificato per la sessione XMLA (XML for Analysis). Se non è disponibile alcuna didascalia, questo elemento contiene il nome univoco del membro.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
