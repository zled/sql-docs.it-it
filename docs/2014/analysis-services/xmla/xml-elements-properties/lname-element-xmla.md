---
title: Elemento LName (XMLA) | Microsoft Docs
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
- LName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#LName
- http://schemas.microsoft.com/analysisservices/2003/engine#LName
- microsoft.xml.analysis.lname
helpviewer_keywords:
- LName element
ms.assetid: 2c8c2fa9-cb2d-44ea-b253-5e6ff61f1b66
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 13eb12010ab201067494cb04c598301f4f8c44e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255193"
---
# <a name="lname-element-xmla"></a>Elemento LName (XMLA)
  Contiene informazioni sui nomi di livello univoci per l'elemento padre [HierarchyInfo](hierarchyinfo-element-xmla.md) oppure [membro](member-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <LName>...</LName>  
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
 Per gli elementi `HierarchyInfo`, questo elemento contiene il nome della proprietà che fornisce i nomi di livello univoci della gerarchia. Il valore è equivalente alla proprietà LEVEL_UNIQUE_NAME definita per i set di righe dell'asse nella specifica OLE DB per OLAP.  
  
 Per gli elementi `Member`, questo elemento contiene il nome univoco del livello nella gerarchia che include il membro rappresentato dall'elemento padre `Member`.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
