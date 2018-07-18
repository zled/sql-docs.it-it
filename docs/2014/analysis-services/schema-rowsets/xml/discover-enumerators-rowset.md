---
title: Set di righe DISCOVER_ENUMERATORS | Microsoft Docs
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
- DISCOVER_ENUMERATORS
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_ENUMERATORS rowset
ms.assetid: ddc7b13c-3135-4419-8166-eddd459167da
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 328d37a9d010388c0cb8d0e7e9d251601e35f949
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37302711"
---
# <a name="discoverenumerators-rowset"></a>Set di righe DISCOVER_ENUMERATORS
  Restituisce un elenco di nomi, tipi di dati e valori di enumerazione di enumeratori supportati dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) per un'origine dati specifica. Il provider XMLA pubblica tutte le costanti di enumerazione che riconosce.  
  
 Se si chiama il [Discover](../../xmla/xml-elements-methods-discover.md) metodo con il `DISCOVER_ENUMERATORS` il valore di enumerazione nel [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md) elemento, il `Discover` metodo restituisce il `DISCOVER_ENUMERATORS` set di righe dello schema.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Per ogni enumeratore sono presenti più elementi, uno per ogni valore dell'enumerazione. Il set di righe che rappresenta ogni enumeratore è flat e il nome dell'enumeratore può essere ripetuto per gli elementi appartenenti alla stessa enumerazione.  
  
 Il `DISCOVER_ENUMERATORS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`EnumName`|`DBTYPE_WSTR`||Nome dell'enumeratore che contiene un set di valori.|  
|`EnumDescription`|`DBTYPE_WSTR`||Descrizione localizzabile dell'enumeratore. Può essere `NULL`.|  
|`EnumType`|`DBTYPE_WSTR`||Tipo di dati dei valori di enumerazione.|  
|`ElementName`|`DBTYPE_WSTR`||Nome di uno degli elementi di valore nell'enumeratore impostato.<br /><br /> Esempio: `TDP`|  
|`ElementDescription`|`DBTYPE_WSTR`||(Facoltativo) Descrizione localizzabile dell'elemento. Può essere `NULL`.|  
|`ElementValue`|`DBTYPE_WSTR`||Valore dell'elemento. Può essere `NULL`.<br /><br /> Esempio: `01`|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_ENUMERATORS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`EnumName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
