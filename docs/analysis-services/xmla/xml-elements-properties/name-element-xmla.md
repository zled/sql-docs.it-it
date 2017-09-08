---
title: Nome di elemento (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Name Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5251f22e39932f49fa4c512b8c5b76a2bf0e7af9
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="name-element-xmla"></a>Elemento Name (XMLA)
  Contiene il nome di un membro dell'attributo per l'elemento padre [attributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md) o [traduzione](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Cardinalità|  
|------------------------|-----------------|  
|[Attribute](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)|1-1: elemento obbligatorio visualizzato una sola volta.|  
|[Conversione](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributo](../../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md), [traduzione](../../../analysis-services/xmla/xml-elements-properties/translation-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Per **attributo** elementi, il **nome** elemento contiene il nome del membro dell'attributo da inserire o aggiornare durante, rispettivamente, il **inserire** o **Aggiornamento** comando.  
  
 Per **traduzione** elementi, il **nome** elemento contiene la didascalia del membro dell'attributo, nel linguaggio specificato per il **Language** dell'elemento padre  **Conversione** oggetto. Se il **nome** elemento non è specificato o contiene una stringa vuota, il valore della **nome** elemento per il **attributo** elemento che contiene il  **Conversione** viene utilizzato l'elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Inserisci elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Elemento di linguaggio &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/language-element-xmla.md)   
 [Elemento Update &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
