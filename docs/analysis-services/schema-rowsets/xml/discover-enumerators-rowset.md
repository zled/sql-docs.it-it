---
title: Set di righe DISCOVER_ENUMERATORS | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DISCOVER_ENUMERATORS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_ENUMERATORS rowset
ms.assetid: ddc7b13c-3135-4419-8166-eddd459167da
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 66ad0a7e82cb1b74108a1275a9e0a7363183d051
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discoverenumerators-rowset"></a>Set di righe DISCOVER_ENUMERATORS
  Restituisce un elenco di nomi, tipi di dati e valori di enumerazione di enumeratori supportati dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) per un'origine dati specifica. Il provider XMLA pubblica tutte le costanti di enumerazione che riconosce.  
  
 Se si chiama il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo con il **DISCOVER_ENUMERATORS** valore di enumerazione nel [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, il **Discover** metodo restituisce il **DISCOVER_ENUMERATORS** set di righe dello schema.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Per ogni enumeratore sono presenti più elementi, uno per ogni valore dell'enumerazione. Il set di righe che rappresenta ogni enumeratore è flat e il nome dell'enumeratore può essere ripetuto per gli elementi appartenenti alla stessa enumerazione.  
  
 Il **DISCOVER_ENUMERATORS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**Nomeenumerazione**|**DBTYPE_WSTR**||Nome dell'enumeratore che contiene un set di valori.|  
|**EnumDescription**|**DBTYPE_WSTR**||Descrizione localizzabile dell'enumeratore. Può essere **NULL**.|  
|**EnumType**|**DBTYPE_WSTR**||Tipo di dati dei valori di enumerazione.|  
|**ElementName**|**DBTYPE_WSTR**||Nome di uno degli elementi di valore nell'enumeratore impostato.<br /><br /> Esempio: **TDP**|  
|**ElementDescription**|**DBTYPE_WSTR**||(Facoltativo) Descrizione localizzabile dell'elemento. Può essere **NULL**.|  
|**ElementValue**|**DBTYPE_WSTR**||Valore dell'elemento. Può essere **NULL**.<br /><br /> Esempio: **01**|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_ENUMERATORS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**Nomeenumerazione**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

