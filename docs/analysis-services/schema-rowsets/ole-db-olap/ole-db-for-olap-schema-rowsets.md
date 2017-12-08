---
title: OLE DB per OLAP Schema Rowsets | Documenti Microsoft
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f06af3341034ccc9ddebe1ac6a130be705bdd0cd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="ole-db-for-olap-schema-rowsets"></a>Set di righe dello schema OLE DB per OLAP
  Il provider di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) supporta i set di righe dello schema OLE DB per OLAP seguenti.  
  
> [!NOTE]  
>  Per verificare se un provider dell'origine dati supporta un set di righe, utilizzare il **DISCOVER_ENUMERATIONS** set di righe con la [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo.  
  
 È inoltre possibile trovare informazioni dettagliate su questi set di righe, cercare l'argomento "Rowset dello Schema OLAP", in MSDN Library in questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkId=15426).  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Set di righe dello schema<sup>1</sup>|Description|  
|-------------------------------|-----------------|  
|[Set di righe DISCOVER_INSTANCES](../../../analysis-services/schema-rowsets/ole-db-olap/discover-instances-rowset.md)|Descrive le istanze nel server.|  
|[Set di righe DISCOVER_KEYWORDS &#40; OLE DB per OLAP &#41;](../../../analysis-services/schema-rowsets/ole-db-olap/discover-keywords-rowset-ole-db-for-olap.md)|Enumera un elenco di parole riservate dal provider.|  
|[Set di righe MDSCHEMA_ACTIONS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-actions-rowset.md)|Descrive le azioni che possono essere disponibili per l'applicazione client.|  
|[Set di righe MDSCHEMA_CUBES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-cubes-rowset.md)|Descrive la struttura dei cubi all'interno di un database.|  
|[Set di righe MDSCHEMA_DIMENSIONS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-dimensions-rowset.md)|Descrive le dimensioni condivise e private all'interno di un database.|  
|[Set di righe MDSCHEMA_FUNCTIONS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-functions-rowset.md)|Descrive le funzioni disponibili per le applicazioni client connesse al database.|  
|[Set di righe MDSCHEMA_HIERARCHIES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-hierarchies-rowset.md)|Descrive ogni gerarchia contenuta in una determinata dimensione.|  
|[Set di righe MDSCHEMA_INPUT_DATASOURCES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-input-datasources-rowset.md)|Descrive le origini dati definite all'interno del database.|  
|[Set di righe MDSCHEMA_KPIS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-kpis-rowset.md)|Descrive gli indicatori di prestazioni chiave (KPI) all'interno di un database.|  
|[Set di righe MDSCHEMA_LEVELS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-levels-rowset.md)|Descrive ogni livello all'interno di una determinata gerarchia.|  
|[Set di righe MDSCHEMA_MEASUREGROUP_DIMENSIONS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset.md)|Enumera le dimensioni dei gruppi di misure.|  
|[Set di righe MDSCHEMA_MEASUREGROUPS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measuregroups-rowset.md)|Descrive i gruppi di misure all'interno di un database.|  
|[Set di righe MDSCHEMA_MEASURES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-measures-rowset.md)|Descrive ogni misura di un cubo.|  
|[Set di righe MDSCHEMA_MEMBERS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-members-rowset.md)|Descrive i membri all'interno di un database.|  
|[Set di righe MDSCHEMA_PROPERTIES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)|Descrive le proprietà dei membri all'interno di un database.|  
|[Set di righe MDSCHEMA_SETS](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-sets-rowset.md)|Descrive i set attualmente definiti in un database, inclusi i set con ambito sessione.|  
  
 <sup>1</sup> tutte le righe dello schema elencate di seguito sono supportate dal provider dell'origine dati MSOLAP per il [!INCLUDE[msCoName](../../../includes/msconame-md.md)] provider XMLA.  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe DISCOVER_ENUMERATORS](../../../analysis-services/schema-rowsets/xml/discover-enumerators-rowset.md)   
 [Set di righe dello schema di Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
