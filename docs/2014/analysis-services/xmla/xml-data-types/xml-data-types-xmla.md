---
title: Tipi di dati XML (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d7a21691474e890ba8614715b18e972d1353b2c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070117"
---
# <a name="xml-data-types-xmla"></a>Tipi di dati XML (XMLA)
  Oltre al tipo primitivo standard e ai tipi derivati definiti dal requisito XML 1.0, la specifica XML for Analysis (XMLA) 1.1 definisce tipi di dati aggiuntivi per supportare la rappresentazione di dati multidimensionali e tabulari.  
  
 XMLA utilizza i tipi di dati elencati nella seguente tabella.  
  
|Tipi di dati|Description|  
|----------------|-----------------|  
|Boolean|Il tipo di dati `boolean` XML standard.|  
|Decimal|Il tipo di dati `decimal` XML standard.|  
|[EmptyResult](emptyresult-data-type-xmla.md)|Un spazio dei nomi sull'elemento `root`. Questo spazio dei nomi viene restituito quando un comando XMLA non restituisce un risultato perché il comando XMLA non restituisce normalmente un risultato o perché si è verificato un errore di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza durante l'esecuzione del comando XMLA.|  
|[EnumString](enumstring-data-type-xmla.md)|Un set di costanti della stringa denominate per un enumeratore specificato.|  
|Valore intero|Il tipo di dati `int` XML standard.|  
|[MDDataSet](mddataset-data-type-xmla.md)|Dati multidimensionali restituiti dal *risultato* parametro del [Execute](../xml-elements-methods-execute.md) metodo.|  
|[Set di risultati](resultset-data-type-xmla.md)|Un set di risultati di XML autodescrittivo restituito dal metodo `Execute`.|  
|[Rowset](rowset-data-type-xmla.md)|Restituisce righe da un'origine dati, strutturate da un XML schema incorporato, il [Discover](../xml-elements-methods-discover.md) metodo.|  
|String|Il tipo di dati `string` XML.|  
|UnsignedInt|Il tipo di schema `unsignedInt` XML.|  
  
 Per descrizioni complete dei tipi di dati XML standard, vedere il requisito candidato di World Wide Web Consortium (WC3).  
  
## <a name="see-also"></a>Vedere anche  
 [Elementi XML &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [XML for Analysis &#40;XMLA&#41; riferimento](../xml-for-analysis-xmla-reference.md)  
  
  