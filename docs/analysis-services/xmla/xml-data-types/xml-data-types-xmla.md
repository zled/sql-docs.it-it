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
ms.openlocfilehash: 07bb4d7212d586ed533afc129ac9e1643a7c7dc1
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="xml-data-types-xmla"></a>Tipi di dati XML (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Oltre al tipo primitivo standard e ai tipi derivati definiti dal requisito XML 1.0, la specifica XML for Analysis (XMLA) 1.1 definisce tipi di dati aggiuntivi per supportare la rappresentazione di dati multidimensionali e tabulari.  
  
 XMLA utilizza i tipi di dati elencati nella seguente tabella.  
  
|Tipi di dati|Description|  
|----------------|-----------------|  
|Boolean|Il codice XML standard **booleano** tipo di dati.|  
|Decimal|Il codice XML standard **decimale** tipo di dati.|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|Uno spazio dei nomi nel **radice** elemento. Questo spazio dei nomi viene restituito quando un comando XMLA non restituisce un risultato perché il comando XMLA non restituisce normalmente un risultato o perché si è verificato un errore di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza durante l'esecuzione del comando XMLA.|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|Un set di costanti della stringa denominate per un enumeratore specificato.|  
|Integer|Il codice XML standard **int** tipo di dati.|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|Dati multidimensionali restituiti dal *risultato* parametro del [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.|  
|[Set di risultati](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|Il set restituito da un file XML autodescrittivo risultati il **Execute** metodo.|  
|[Rowset](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|Le righe da un'origine dati, strutturate da un XML schema incorporato, restituito dal [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo.|  
|String|Il codice XML **stringa** tipo di dati.|  
|UnsignedInt|Il codice XML **unsignedInt** tipo di schema.|  
  
 Per descrizioni complete dei tipi di dati XML standard, vedere il requisito candidato di World Wide Web Consortium (WC3).  
  
## <a name="see-also"></a>Vedere anche  
 [Gli elementi XML & #40; XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML for Analysis & #40; XMLA & #41; Riferimento](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
