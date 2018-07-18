---
title: Set di righe DISCOVER_KEYWORDS (XMLA) | Microsoft Docs
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a8be22c5132ed85ecb515ccadce20ecd593818a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241551"
---
# <a name="discoverkeywords-rowset-xmla"></a>Set di righe DISCOVER_KEYWORDS (XMLA)
  Restituisce informazioni sulle parole chiave riservate dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA).  
  
 Se si chiama il [Discover](../../xmla/xml-elements-methods-discover.md) metodo con il `DISCOVER_KEYWORDS` il valore di enumerazione nel [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) elemento, il `Discover` metodo restituisce il `DISCOVER_KEYWORDS` set di righe.  
  
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
  
  
