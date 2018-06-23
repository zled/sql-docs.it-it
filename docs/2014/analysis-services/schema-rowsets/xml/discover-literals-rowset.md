---
title: Set di righe DISCOVER_LITERALS | Documenti Microsoft
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
api_name:
- DISCOVER_LITERALS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a4643ab803f3e6a7d63c4172423e909b6badd64b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066782"
---
# <a name="discoverliterals-rowset"></a>Set di righe DISCOVER_LITERALS
  Restituisce informazioni sui valori letterali, inclusi tipi e valori di dati, supportati dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA (XML for Analysis).  
  
 Se si chiama il [Discover](../../xmla/xml-elements-methods-discover.md) metodo con il `DISCOVER_LITERALS` valore di enumerazione nel [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) elemento, il `Discover` metodo restituisce il `DISCOVER_LITERALS` set di righe.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_LITERALS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`LiteralName`|`DBTYPE_WSTR`||Nome del valore letterale descritto nella riga.<br /><br /> Ad esempio: `DBLITERAL_LIKE_PERCENT`|  
|`LiteralValue`|`DBTYPE_WSTR`||Valore letterale effettivo.<br /><br /> Se ad esempio `LiteralName` è `DBLITERAL_LIKE_PERCENT` e il carattere `%` corrisponde a zero o a più caratteri in una clausola LIKE, il valore della colonna `LiteralValue` è "`%`".|  
|`LiteralInvalidChars`|`DBTYPE_WSTR`||Caratteri non validi nel valore letterale.<br /><br /> Se ad esempio i nomi delle tabelle possono contenere caratteri diversi da quelli numerici, questa stringa sarà "`0123456789`".|  
|`LiteralInvalidStartingChars`|`DBTYPE_WSTR`||Caratteri non validi come primo carattere del valore letterale. Se il valore letterale può iniziare con qualsiasi carattere valido, questo sarà `null`.|  
|`LiteralMaxLength`|`DBTYPE_I4`||Numero massimo di caratteri nel valore letterale. Se non è presente un valore massimo o tale valore è sconosciuto, il valore sarà –1.|  
|`LiteralNameEnumValue`|`DBTYPE_I4`|||  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_LITERALS` può essere limitato nelle colonne della tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`LiteralName`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i set di righe dello Schema](xml-for-analysis-schema-rowsets.md)   
 [Set di righe DISCOVER_KEYWORDS &#40;XMLA&#41;](discover-keywords-rowset-xmla.md)  
  
  