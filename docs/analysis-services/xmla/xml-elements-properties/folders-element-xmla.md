---
title: Elemento Folders (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Folders Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.folders
- http://schemas.microsoft.com/analysisservices/2003/engine#Folders
- urn:schemas-microsoft-com:xml-analysis#Folders
helpviewer_keywords: Folders element
ms.assetid: fefb0469-22ea-4804-8dc3-9c49825b32f1
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 452f501b4189866c2257d871c581e0fd88313426
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="folders-element-xmla"></a>Elemento Folders (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contiene una raccolta di [cartella](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md) elementi utilizzati dall'elemento padre [percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) elemento durante un [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) o [Sincronizza](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Location>  
   ...  
   <Folders>  
      <Folder>...</Folder>  
   </Folders>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno (raccolta)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Elementi figlio|[Cartella](../../../analysis-services/xmla/xml-elements-properties/folder-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>Vedere anche  
 [Ripristinare l'elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Sincronizzare elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
