---
title: Elemento UName (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- UName Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#UName
- urn:schemas-microsoft-com:xml-analysis#UName
- microsoft.xml.analysis.uname
helpviewer_keywords:
- UName element
ms.assetid: b4916d44-cf77-4d4c-b4e5-a0a98192d057
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d348fe5f1474b44df2bd765e7c9d7db2df4c809e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48083621"
---
# <a name="uname-element-xmla"></a>Elemento UName (XMLA)
  Contiene il nome univoco dell'elemento padre [HierarchyInfo](hierarchyinfo-element-xmla.md) oppure [membro](member-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <UName>...</UName>  
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
 Per gli elementi `HierarchyInfo`, l'elemento `UName` contiene il nome della proprietà che fornisce i nomi del membro univoci della gerarchia. Il valore è equivalente alla proprietà MEMBER_UNIQUE_NAME definita per i set di righe dell'asse in OLE DB per la specifica OLAP.  
  
 Per gli elementi `Member`, l'elemento `UName` contiene il nome univoco dell'elemento `Member` padre.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
