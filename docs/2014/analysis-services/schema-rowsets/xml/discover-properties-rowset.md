---
title: Set di righe DISCOVER_PROPERTIES | Documenti Microsoft
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
- DISCOVER_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_PROPERTIES rowset
ms.assetid: 3e2b50e2-3855-4091-8b02-4968e8e57d4c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: af566467345e29362a7b2fdd2c5bda04a35a6dd5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156090"
---
# <a name="discoverproperties-rowset"></a>Set di righe DISCOVER_PROPERTIES
  Restituisce un elenco di informazioni e valori sulle proprietà standard e specifiche del provider supportate dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) per l'origine dati specificata. Le proprietà non supportate non sono elencate nel set di risultati restituito.  
  
 Se si chiama il [Discover](../../xmla/xml-elements-methods-discover.md) metodo con il `DISCOVER_PROPERTIES` valore di enumerazione nel [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) elemento, il `Discover` metodo restituisce il `DISCOVER_PROPERTIES` set di righe...  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_PROPERTIES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Tipo|Length|Description|  
|-----------------|----------|------------|-----------------|  
|`PropertyName`|`DBTYPE_WSTR`||Nome della proprietà.|  
|`PropertyDescription`|`DBTYPE_WSTR`||Descrizione di testo localizzabile della proprietà. Potrebbe restituire `NULL`.|  
|`PropertyType`|`DBTYPE_WSTR`||Tipo di dati XML della proprietà.<br /><br /> Potrebbe restituire `NULL`.|  
|`PropertyAccessType`|`DBTYPE_WSTR`||Accesso alla proprietà. Il valore può essere `Read`, `Write` o `ReadWrite`.|  
|`IsRequired`|`DBTYPE_BOOL`||Valore booleano che indica se è necessaria una proprietà.<br /><br /> True se una proprietà è necessaria; false se non è necessaria.<br /><br /> Potrebbe restituire `NULL`.|  
|`Value`|`DBTYPE_WSTR`||Valore corrente della proprietà.<br /><br /> Potrebbe restituire `NULL`.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_PROPERTIES` può essere limitato sulla colonna elencata nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`PropertyName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  