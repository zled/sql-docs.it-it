---
title: Set di righe DISCOVER_KEYWORDS (XMLA) | Documenti Microsoft
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
- DISCOVER_KEYWORDS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_KEYWORDS rowset
ms.assetid: 99945e53-3a1b-4d7b-9aff-712977db8b2d
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df7fd7c6bf7dbe9ebd0bb9057b5c82dc351afab3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065233"
---
# <a name="discoverkeywords-rowset-xmla"></a>Set di righe DISCOVER_KEYWORDS (XMLA)
  Restituisce informazioni sulle parole chiave riservate dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA).  
  
 Se si chiama il [Discover](../../xmla/xml-elements-methods-discover.md) metodo con il `DISCOVER_KEYWORDS` valore di enumerazione nel [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) elemento, il `Discover` metodo restituisce il `DISCOVER_KEYWORDS` set di righe.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_KEYWORDS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`Keyword`|`DBTYPE_WSTR`||Elenco di tutte le parole chiave riservate da un provider.<br /><br /> Esempio: `AND`|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_KEYWORDS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`Keyword`|`DBTYPE_WSTR`|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i set di righe dello Schema](xml-for-analysis-schema-rowsets.md)   
 [Set di righe DISCOVER_LITERALS](discover-literals-rowset.md)  
  
  