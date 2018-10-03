---
title: OLE DB per i set di righe dello Schema OLAP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- schema rowsets [Analysis Services], OLE DB for OLAP
- OLE DB for OLAP schema rowsets
- schema rowsets [OLE DB for OLAP]
- rowsets [Analysis Services], OLE DB for OLAP
ms.assetid: 5fad3ecc-407c-4148-862e-ea6119cc7480
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd2e29e03617ccc3929ca0845e2b703e406cbfb2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172971"
---
# <a name="ole-db-for-olap-schema-rowsets"></a>Set di righe dello schema OLE DB per OLAP
  Il provider di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) supporta i set di righe dello schema OLE DB per OLAP seguenti.  
  
> [!NOTE]  
>  Per verificare se un provider dell'origine dati specifica supporta un set di righe, usare il `DISCOVER_ENUMERATIONS` set di righe con i [Discover](../../xmla/xml-elements-methods-discover.md) (metodo).  
  
 È anche possibile trovare informazioni dettagliate su questi set di righe eseguendo una ricerca per l'argomento "Rowset dello Schema OLAP", in MSDN Library all'indirizzo ciò [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkId=15426).  
  
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
  
  
