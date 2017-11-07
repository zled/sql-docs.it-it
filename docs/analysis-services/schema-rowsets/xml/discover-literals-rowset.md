---
title: Set di righe DISCOVER_LITERALS | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DISCOVER_LITERALS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_LITERALS rowset
ms.assetid: 1bf0a2e2-a419-4c25-b271-37dfa44de2ea
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 95037ba44f93df3aa0dbe5ad4279ca1ca9a1bf28
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discoverliterals-rowset"></a>Set di righe DISCOVER_LITERALS
  Restituisce informazioni sui valori letterali, inclusi tipi e valori di dati, supportati dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA (XML for Analysis).  
  
 Se si chiama il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo con il **DISCOVER_LITERALS** valore di enumerazione nel [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, il **Discover** metodo restituisce il **DISCOVER_LITERALS** set di righe.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_LITERALS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**LiteralName**|**DBTYPE_WSTR**||Nome del valore letterale descritto nella riga.<br /><br /> Ad esempio: **DBLITERAL_LIKE_PERCENT**|  
|**LiteralValue**|**DBTYPE_WSTR**||Valore letterale effettivo.<br /><br /> Ad esempio, se **LiteralName** è **DBLITERAL_LIKE_PERCENT** e il carattere di percentuale (**%**) consente di ricercare zero o più caratteri in una clausola LIKE, il valore del **LiteralValue** colonna è "**%**".|  
|**LiteralInvalidChars**|**DBTYPE_WSTR**||Caratteri non validi nel valore letterale.<br /><br /> Ad esempio, se i nomi di tabella possono contenere qualsiasi elemento diverso da un carattere numerico, questa stringa è "**0123456789**".|  
|**LiteralInvalidStartingChars**|**DBTYPE_WSTR**||Caratteri non validi come primo carattere del valore letterale. Se il valore letterale può iniziare con qualsiasi carattere valido, si tratta di **null**.|  
|**LiteralMaxLength**|**DBTYPE_I4**||Numero massimo di caratteri nel valore letterale. Se non è presente un valore massimo o tale valore è sconosciuto, il valore sarà –1.|  
|**LiteralNameEnumValue**|**DBTYPE_I4**|||  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_LITERALS** set di righe può essere limitato sulle colonne nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**LiteralName**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Set di righe DISCOVER_KEYWORDS &#40; XMLA &#41;](../../../analysis-services/schema-rowsets/xml/discover-keywords-rowset-xmla.md)  
  
  

