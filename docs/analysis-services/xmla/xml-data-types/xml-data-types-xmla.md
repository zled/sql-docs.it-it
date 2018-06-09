---
title: Tipi di dati XML (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c52717a6f061f4708b2d3e46c6d34f837b2039af
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34573783"
---
# <a name="xml-data-types-xmla"></a>Tipi di dati XML (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Oltre al tipo primitivo standard e ai tipi derivati definiti dal requisito XML 1.0, la specifica XML for Analysis (XMLA) 1.1 definisce tipi di dati aggiuntivi per supportare la rappresentazione di dati multidimensionali e tabulari.  
  
 XMLA utilizza i tipi di dati elencati nella seguente tabella.  
  
|Tipi di dati|Description|  
|----------------|-----------------|  
|Boolean|Il codice XML standard **booleano** tipo di dati.|  
|Decimal|Il codice XML standard **decimale** tipo di dati.|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|Uno spazio dei nomi nel **radice** elemento. Questo spazio dei nomi viene restituito quando un comando XMLA non restituisce un risultato perché il comando XMLA non restituisce normalmente un risultato o perché si è verificato un errore nell'istanza di Analysis Services durante l'esecuzione del comando XMLA.|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|Un set di costanti della stringa denominate per un enumeratore specificato.|  
|Valore intero|Il codice XML standard **int** tipo di dati.|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|Dati multidimensionali restituiti dal *risultato* parametro del [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.|  
|[Set di risultati](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|Il set restituito da un file XML autodescrittivo risultati il **Execute** metodo.|  
|[Rowset](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|Le righe da un'origine dati, strutturate da un XML schema incorporato, restituito dal [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo.|  
|String|Il codice XML **stringa** tipo di dati.|  
|UnsignedInt|Il codice XML **unsignedInt** tipo di schema.|  
  
 Per descrizioni complete dei tipi di dati XML standard, vedere il requisito candidato di World Wide Web Consortium (WC3).  
  
## <a name="see-also"></a>Vedere anche
 [Elementi XML &#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML for Analysis &#40;XMLA&#41; riferimento](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
