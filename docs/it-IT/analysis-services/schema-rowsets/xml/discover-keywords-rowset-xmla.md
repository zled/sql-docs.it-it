---
title: Set di righe DISCOVER_KEYWORDS (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: 0a8933c872bcc0947e8bff34cf3fbbc57394b9cf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="discoverkeywords-rowset-xmla"></a>Set di righe DISCOVER_KEYWORDS (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [XML for Analysis i set di righe dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Set di righe DISCOVER_LITERALS](../../../analysis-services/schema-rowsets/xml/discover-literals-rowset.md)  
  
  
