---
title: Chiave di elemento (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Key Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Key
- urn:schemas-microsoft-com:xml-analysis#Key
- microsoft.xml.analysis.key
helpviewer_keywords: Key element
ms.assetid: 09d3cd48-49f7-4b58-b8bb-ca75b81bb02f
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2e6c77841fa78b1ad2c866abc5c3aea5af50ef27
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="key-element-xmla"></a>Elemento Key (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contiene un valore di chiave membro per un membro dell'attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Keys>  
   ...  
   <Key>...</Key>  
   ...  
</Keys>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Qualsiasi|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Chiavi](../../../analysis-services/xmla/xml-elements-properties/keys-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il tipo di dati utilizzato da questo elemento deve corrispondere al tipo di dati della colonna chiave appropriata dell'attributo specificato. Se **chiave** elementi non vengono specificati per un elemento padre **attributo** elemento, il **AttributeName** e **nome** elementi specificati di padre **attributo** elemento vengono usati per identificare il membro dell'attributo da modificare.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Attribute &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)   
 [Elemento AttributeName &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)   
 [Eliminare l'elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [Inserisci elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Elemento KeyColumn &#40; ASSL &#41;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)   
 [Elemento Update &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [In elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
