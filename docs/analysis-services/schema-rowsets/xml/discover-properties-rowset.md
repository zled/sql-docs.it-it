---
title: Set di righe DISCOVER_PROPERTIES | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8752af7b67b69659ec3d9a348b4ec7c647f41c55
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="discoverproperties-rowset"></a>Set di righe DISCOVER_PROPERTIES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Restituisce un elenco di informazioni e valori sulle proprietà standard e specifiche del provider supportate dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) per l'origine dati specificata. Le proprietà non supportate non sono elencate nel set di risultati restituito.  
  
 Se si chiama il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo con il **DISCOVER_PROPERTIES** valore di enumerazione nel [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, il **Discover** metodo restituisce il **DISCOVER_PROPERTIES** set di righe...  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_PROPERTIES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Tipo|Lunghezza|Description|  
|-----------------|----------|------------|-----------------|  
|**propertyName**|**DBTYPE_WSTR**||Nome della proprietà.|  
|**PropertyDescription**|**DBTYPE_WSTR**||Descrizione di testo localizzabile della proprietà. Può restituire **NULL**.|  
|**PropertyType**|**DBTYPE_WSTR**||Tipo di dati XML della proprietà.<br /><br /> Può restituire **NULL**.|  
|**Tipoaccessoproprietà**|**DBTYPE_WSTR**||Accesso alla proprietà. Il valore può essere **lettura**, **scrivere**, o **ReadWrite**.|  
|**IsRequired**|**DBTYPE_BOOL**||Valore booleano che indica se è necessaria una proprietà.<br /><br /> True se una proprietà è necessaria; false se non è necessaria.<br /><br /> Può restituire **NULL**.|  
|**Valore**|**DBTYPE_WSTR**||Valore corrente della proprietà.<br /><br /> Può restituire **NULL**.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_PROPERTIES** righe può essere limitato sulla colonna elencata nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**propertyName**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
