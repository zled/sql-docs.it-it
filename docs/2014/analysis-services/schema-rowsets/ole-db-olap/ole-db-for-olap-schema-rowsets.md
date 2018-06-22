---
title: OLE DB per OLAP Schema Rowsets | Documenti Microsoft
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
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 898749e17cb5b85e61a2b2c3a94b7247a7ab219b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068157"
---
# <a name="ole-db-for-olap-schema-rowsets"></a>Set di righe dello schema OLE DB per OLAP
  Il provider di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) supporta i set di righe dello schema OLE DB per OLAP seguenti.  
  
> [!NOTE]  
>  Per verificare se un provider dell'origine dati specifica supporta un set di righe, utilizzare il `DISCOVER_ENUMERATIONS` set di righe con la [Discover](../../xmla/xml-elements-methods-discover.md) metodo.  
  
 È anche possibile trovare informazioni dettagliate su questi set di righe, cercare l'argomento "Rowset dello Schema OLAP", in MSDN Library in questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkId=15426).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Set di righe dello schema<sup>1</sup>|Description|  
|-------------------------------|-----------------|  
|[Set di righe DISCOVER_INSTANCES](discover-instances-rowset.md)|Descrive le istanze nel server.|  
|[Set di righe DISCOVER_KEYWORDS &#40;OLE DB per OLAP&#41;](discover-keywords-rowset-ole-db-for-olap.md)|Enumera un elenco di parole riservate dal provider.|  
|[Set di righe MDSCHEMA_ACTIONS](mdschema-actions-rowset.md)|Descrive le azioni che possono essere disponibili per l'applicazione client.|  
|[Set di righe MDSCHEMA_CUBES](mdschema-cubes-rowset.md)|Descrive la struttura dei cubi all'interno di un database.|  
|[Set di righe MDSCHEMA_DIMENSIONS](mdschema-dimensions-rowset.md)|Descrive le dimensioni condivise e private all'interno di un database.|  
|[Set di righe MDSCHEMA_FUNCTIONS](mdschema-functions-rowset.md)|Descrive le funzioni disponibili per le applicazioni client connesse al database.|  
|[Set di righe MDSCHEMA_HIERARCHIES](mdschema-hierarchies-rowset.md)|Descrive ogni gerarchia contenuta in una determinata dimensione.|  
|[Set di righe MDSCHEMA_INPUT_DATASOURCES](mdschema-input-datasources-rowset.md)|Descrive le origini dati definite all'interno del database.|  
|[Set di righe MDSCHEMA_KPIS](mdschema-kpis-rowset.md)|Descrive gli indicatori di prestazioni chiave (KPI) all'interno di un database.|  
|[Set di righe MDSCHEMA_LEVELS](mdschema-levels-rowset.md)|Descrive ogni livello all'interno di una determinata gerarchia.|  
|[Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS](mdschema-measuregroup-dimensions-rowset.md)|Enumera le dimensioni dei gruppi di misure.|  
|[Set di righe MDSCHEMA_MEASUREGROUPS](mdschema-measuregroups-rowset.md)|Descrive i gruppi di misure all'interno di un database.|  
|[Set di righe MDSCHEMA_MEASURES](mdschema-measures-rowset.md)|Descrive ogni misura di un cubo.|  
|[Set di righe MDSCHEMA_MEMBERS](mdschema-members-rowset.md)|Descrive i membri all'interno di un database.|  
|[Set di righe MDSCHEMA_PROPERTIES](mdschema-properties-rowset.md)|Descrive le proprietà dei membri all'interno di un database.|  
|[Set di righe MDSCHEMA_SETS](mdschema-sets-rowset.md)|Descrive i set attualmente definiti in un database, inclusi i set con ambito sessione.|  
  
 <sup>1</sup> tutte le righe dello schema elencati di seguito sono supportate dal provider dell'origine dati MSOLAP per il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] provider XMLA.  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe DISCOVER_ENUMERATORS](../xml/discover-enumerators-rowset.md)   
 [Set di righe dello schema di Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  