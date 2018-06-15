---
title: Set di righe DISCOVER_ENUMERATORS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3c67c7e2a87931aee05af6fcdadabb3263cf66a8
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028522"
---
# <a name="discoverenumerators-rowset"></a>Set di righe DISCOVER_ENUMERATORS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
  
