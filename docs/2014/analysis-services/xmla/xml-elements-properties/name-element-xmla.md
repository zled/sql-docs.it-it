---
title: Nome di elemento (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
caps.latest.revision: 12
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: d3ae469cc1a02a02dc2bdb2ff7d6db7f75a46a69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167122"
---
# <a name="name-element-xmla"></a>Elemento Name (XMLA)
  Contiene il nome di un membro dell'attributo per l'elemento padre [attributo](attribute-element-xmla.md) oppure [traduzione](translation-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Predecessore o padre:|Cardinalità|  
|[Attribute](attribute-element-xmla.md)|1-1: elemento obbligatorio visualizzato una sola volta.|  
|[Conversione](translation-element-xmla.md)|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributo](attribute-element-xmla.md), [traduzione](translation-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Per gli elementi `Attribute`, l'elemento `Name` contiene il nome del membro dell'attributo da inserire o aggiornare durante, rispettivamente, il comando `Insert` o `Update`.  
  
 Per gli elementi `Translation`, l'elemento `Name` contiene la didascalia del membro dell'attributo, nel linguaggio specificato dall'elemento `Language` dell'oggetto `Translation` padre. Se l’elemento `Name` non viene specificato o contiene una stringa vuota, viene utilizzato il valore dell’elemento `Name` per l’elemento `Attribute` che contiene l’elemento `Translation`.  
  
## <a name="see-also"></a>Vedere anche  
 [Inserire l'elemento &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Elemento di linguaggio &#40;XMLA&#41;](language-element-xmla.md)   
 [Aggiornare l'elemento &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  