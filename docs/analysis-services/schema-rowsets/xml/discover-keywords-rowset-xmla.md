---
title: Set di righe DISCOVER_KEYWORDS (XMLA) | Documenti Microsoft
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
- DISCOVER_KEYWORDS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_KEYWORDS rowset
ms.assetid: 99945e53-3a1b-4d7b-9aff-712977db8b2d
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 232bbcfb4d5cf1dfc181a0c6d8879e4390f61a9e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discoverkeywords-rowset-xmla"></a>Set di righe DISCOVER_KEYWORDS (XMLA)
  Restituisce informazioni sulle parole chiave riservate dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA).  
  
 Se si chiama il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo con il **DISCOVER_KEYWORDS** valore di enumerazione nel [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, il **Discover** metodo restituisce il **DISCOVER_KEYWORDS** set di righe.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_KEYWORDS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**Parola chiave**|**DBTYPE_WSTR**||Elenco di tutte le parole chiave riservate da un provider.<br /><br /> Esempio: **AND**|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_KEYWORDS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**Parola chiave**|**DBTYPE_WSTR**|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Set di righe DISCOVER_LITERALS](../../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)  
  
  

