---
title: Chiave di elemento (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3971abfd4c5bbcc90d43d0f427353f24967b0c5d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="key-element-xmla"></a>Elemento Key (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene un valore di chiave membro per un membro dell'attributo.  
  
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
 [Elemento Attribute & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)   
 [Elemento AttributeName & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/attributename-element-xmla.md)   
 [Eliminare l'elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [Inserisci elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Elemento KeyColumn & #40; ASSL & #41;](../../../analysis-services/scripting/objects/keycolumn-element-assl.md)   
 [Elemento Update & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [In elemento & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)   
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
