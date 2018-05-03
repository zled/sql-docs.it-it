---
title: Set di righe DISCOVER_PROPERTIES | Documenti Microsoft
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
- DISCOVER_PROPERTIES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_PROPERTIES rowset
ms.assetid: 3e2b50e2-3855-4091-8b02-4968e8e57d4c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: f37cf116c4d31dbd63ba13b575a91fa042350863
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
  
