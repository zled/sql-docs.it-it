---
title: Elemento LName (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- LName Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#LName
- http://schemas.microsoft.com/analysisservices/2003/engine#LName
- microsoft.xml.analysis.lname
helpviewer_keywords:
- LName element
ms.assetid: 2c8c2fa9-cb2d-44ea-b253-5e6ff61f1b66
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 80457ad8055ea2c69b75f578a7e5fcb486461ef4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lname-element-xmla"></a>Elemento LName (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene informazioni sui nomi di livello univoci per l'elemento padre [HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md) o [membro](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <LName>...</LName>  
   ...  
</HierarchyInfo>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md), [membro](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per **HierarchyInfo** elementi, questo elemento contiene il nome della proprietà che fornisce i nomi di livello univoci della gerarchia. Il valore è equivalente alla proprietà LEVEL_UNIQUE_NAME definita per i set di righe dell'asse nella specifica OLE DB per OLAP.  
  
 Per **membro** elementi, questo elemento contiene il nome univoco del livello nella gerarchia che contiene il membro rappresentato dall'elemento padre **membro** elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
