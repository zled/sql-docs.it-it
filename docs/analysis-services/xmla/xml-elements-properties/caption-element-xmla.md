---
title: Barra del titolo elemento (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Caption Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Caption
- http://schemas.microsoft.com/analysisservices/2003/engine#Caption
- microsoft.xml.analysis.caption
helpviewer_keywords:
- Caption element
ms.assetid: 3d10ee68-98ab-4da0-a409-800dea2f1c32
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 705ab470f248f14637fe859227df201945717e79
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="caption-element-xmla"></a>Elemento Caption (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene informazioni sulla didascalia dell'elemento padre [HierarchyInfo](../../../analysis-services/xmla/xml-elements-properties/hierarchyinfo-element-xmla.md) o [membro](../../../analysis-services/xmla/xml-elements-properties/member-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<HierarchyInfo> <!-- or Member -->  
   ...  
   <Caption>...</Caption>  
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
 Per **HierarchyInfo** elementi, il **didascalia** elemento contiene il nome della proprietà che fornisce il membro didascalie della gerarchia. Il valore è equivalente alla proprietà MEMBER_CAPTION definita per i set di righe dell'asse nella specifica OLE DB per OLAP.  
  
 Per **membro** elementi, il **didascalia** elemento contiene la didascalia dell'elemento padre **membro** nel linguaggio specificato per il codice XML per la sessione Analysis (XMLA). Se non è disponibile alcuna didascalia, questo elemento contiene il nome univoco del membro.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
