---
title: Tipo di dati EmptyResult (XMLA) | Documenti Microsoft
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
- EmptyResult Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EmptyResult
- olapxmla_EmptyResult
- urn:schemas-microsoft-com:xml-analysis#EmptyResult
helpviewer_keywords:
- EmptyResult data type
ms.assetid: 63818123-acbb-4220-9d60-1aa20a7326a1
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: bba727b2d7d612fa59c99665bd16d936da137fb2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169297"
---
# <a name="emptyresult-data-type-xmla"></a>Tipo di dati EmptyResult (XMLA)
  Definisce un tipo di dati derivato che rappresenta un [radice](../xml-elements-properties/root-element-xmla.md) elemento che non restituisce dati da un [Discover](../xml-elements-methods-discover.md) oppure [Execute](../xml-elements-methods-execute.md) chiamata al metodo.  
  
 **Namespace** urn: schemas-microsoft-com: XML-analysis: empty  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<root xmlns="urn:schemas-microsoft-com:xml-analysis:empty">  
   <!-- All elements are inherited from Resultset -->  
</root>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[Set di risultati](resultset-data-type-xmla.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|None|  
|Elementi derivati|[root](../xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Per alcuni comandi XML for Analysis (XMLA) non è previsto che venga restituito un risultato oppure i comandi non sono stati in grado di restituire un risultato a causa di un errore. I comandi XMLA che non restituiscono un risultato restituiscono il tipo di dati `EmptyResult`, un spazio dei nomi nell'elemento `root`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente è rappresentato un elemento `root` restituito per un risultato vuoto.  
  
```  
<return>  
   <root xmlns="urn:schemas-microsoft-com:xml-analysis:empty"/>  
</return>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati XML &#40;XMLA&#41;](xml-data-types-xmla.md)  
  
  