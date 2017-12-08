---
title: Set di righe dello Schema di Analysis Services | Documenti Microsoft
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
ms.topic: article
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- SSAS, data access interfaces
- Analysis Services data access interfaces, schema rowsets
- data access interfaces [Analysis Services]
- XML for Analysis, schema rowsets
- rowsets [Analysis Services], retrieving schema rowsets
- retrieving schema rowsets
- XMLA, schema rowsets
- rowsets [Analysis Services]
- schema rowsets [Analysis Services], retrieving
ms.assetid: 820d4b59-d428-4616-b792-c848e5da407e
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d6e87251e1ab08a87929cd3dba78a584e7c62fd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="analysis-services-schema-rowsets"></a>Set di righe dello schema di Analysis Services
  I set di righe dello schema sono tabelle predefinite che contengono informazioni sugli oggetti di Analysis Services e sullo stato del server, inclusi schema del database, processi, sessioni attive e connessioni in esecuzione nel server. È possibile eseguire una query sulle tabelle del set di righe dello schema in una finestra di script XML/A in SQL Server Management Studio, eseguire una query DMV su un set di righe dello schema o creare un'applicazione personalizzata contenente informazioni sul set di righe dello schema (ad esempio un'applicazione per la creazione di report che recupera l'elenco di dimensioni disponibili che possono essere utilizzate per creare un report).  
  
> [!NOTE]  
>  Se si utilizza set di righe dello schema XML/A script, le informazioni restituite nel *risultato* parametro del [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) metodo strutturato in base il layout delle colonne di set di righe descritti in questo sezione. Il provider [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis (XMLA) supporta i set di righe richiesti dalla specifica XML for Analysis. Il provider XMLA supporta inoltre alcuni dei set di righe dello schema standard per i provider delle origini dati OLE DB, OLE DB per OLAP e OLE DB per Data mining. I set di righe supportati sono descritti negli argomenti seguenti.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[XML per set di righe dello schema di analisi](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|Descrive i set di righe XMLA supportati dal provider XMLA.|  
|[Set di righe dello schema OLE DB](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|Descrive i set di righe dello schema OLE DB supportati dal provider XMLA.|  
|[Set di righe dello schema OLE DB per OLAP](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|Descrive i set di righe dello schema OLE DB per OLAP supportati dal provider XMLA.|  
|[Set di righe dello schema di data mining](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|Descrive i set di righe dello schema di data mining supportati dal provider XMLA.|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai dati di modello multidimensionale &#40; Analysis Services - dati multidimensionali &#41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [Utilizzare DMV per monitorare Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
