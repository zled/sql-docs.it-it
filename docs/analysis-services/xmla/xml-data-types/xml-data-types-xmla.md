---
title: Tipi di dati XML (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: xmla
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 60a10edf09c041b563f15bf5fec83cd1b5ec4ec7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="xml-data-types-xmla"></a>Tipi di dati XML (XMLA)
  Oltre al tipo primitivo standard e ai tipi derivati definiti dal requisito XML 1.0, la specifica XML for Analysis (XMLA) 1.1 definisce tipi di dati aggiuntivi per supportare la rappresentazione di dati multidimensionali e tabulari.  
  
 XMLA utilizza i tipi di dati elencati nella seguente tabella.  
  
|Tipi di dati|Description|  
|----------------|-----------------|  
|Boolean|Il codice XML standard **booleano** tipo di dati.|  
|Decimal|Il codice XML standard **decimale** tipo di dati.|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|Uno spazio dei nomi nel **radice** elemento. Questo spazio dei nomi viene restituito quando un comando XMLA non restituisce un risultato perché il comando XMLA non restituisce normalmente un risultato o perché si è verificato un errore di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza durante l'esecuzione del comando XMLA.|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|Un set di costanti della stringa denominate per un enumeratore specificato.|  
|Valore intero|Il codice XML standard **int** tipo di dati.|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|Dati multidimensionali restituiti dal *risultato* parametro del [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.|  
|[Set di risultati](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|Il set restituito da un file XML autodescrittivo risultati il **Execute** metodo.|  
|[Set di righe](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|Le righe da un'origine dati, strutturate da un XML schema incorporato, restituito dal [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo.|  
|String|Il codice XML **stringa** tipo di dati.|  
|UnsignedInt|Il codice XML **unsignedInt** tipo di schema.|  
  
 Per descrizioni complete dei tipi di dati XML standard, vedere il requisito candidato di World Wide Web Consortium (WC3).  
  
## <a name="see-also"></a>Vedere anche  
 [Gli elementi XML &#40; XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML for Analysis &#40; XMLA &#41; Riferimento](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  

