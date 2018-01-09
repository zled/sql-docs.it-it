---
title: Set di righe DISCOVER_ENUMERATORS | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DISCOVER_ENUMERATORS
apitype: NA
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_ENUMERATORS rowset
ms.assetid: ddc7b13c-3135-4419-8166-eddd459167da
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0be0cb9885cf48911a31ba4181a235eae032094b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="discoverenumerators-rowset"></a>Set di righe DISCOVER_ENUMERATORS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Restituisce un elenco di nomi, tipi di dati e valori di enumerazione di enumeratori supportati dal [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML per il provider Analysis (XMLA) per un'origine dati specifica. Il provider XMLA pubblica tutte le costanti di enumerazione che riconosce.  
  
 Se si chiama il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo con il **DISCOVER_ENUMERATORS** valore di enumerazione nel [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, il **Discover** metodo restituisce il **DISCOVER_ENUMERATORS** set di righe dello schema.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Per ogni enumeratore sono presenti più elementi, uno per ogni valore dell'enumerazione. Il set di righe che rappresenta ogni enumeratore è flat e il nome dell'enumeratore può essere ripetuto per gli elementi appartenenti alla stessa enumerazione.  
  
 Il **DISCOVER_ENUMERATORS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
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
 [XML per set di righe dello schema di analisi](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
