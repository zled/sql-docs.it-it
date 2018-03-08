---
title: Set di righe dello Schema di Analysis Services | Documenti Microsoft
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
ms.topic: article
applies_to:
- SQL Server 2016 Preview
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
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: adb3427f2a482bd32635ccd24eda70a091b2653e
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="analysis-services-schema-rowsets"></a>Set di righe dello schema di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
I set di righe dello schema sono tabelle predefinite che contengono informazioni sugli oggetti di Analysis Services e sullo stato del server, inclusi schema del database, processi, sessioni attive e connessioni in esecuzione nel server. È possibile eseguire una query sulle tabelle del set di righe dello schema in una finestra di script XML/A in SQL Server Management Studio, eseguire una query DMV su un set di righe dello schema o creare un'applicazione personalizzata contenente informazioni sul set di righe dello schema (ad esempio un'applicazione per la creazione di report che recupera l'elenco di dimensioni disponibili che possono essere utilizzate per creare un report).  
  
> [!NOTE]  
>  Se si utilizza set di righe dello schema XML/A script, le informazioni restituite nel *risultato* parametro del [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) metodo strutturato in base il layout delle colonne dei set di righe descritti in questa sezione. Il provider [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis (XMLA) supporta i set di righe richiesti dalla specifica XML for Analysis. Il provider XMLA supporta inoltre alcuni dei set di righe dello schema standard per i provider delle origini dati OLE DB, OLE DB per OLAP e OLE DB per Data mining. I set di righe supportati sono descritti negli argomenti seguenti.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[XML for Analysis i rowset dello Schema](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)|Descrive i set di righe XMLA supportati dal provider XMLA.|  
|[Set di righe dello Schema OLE DB](../../analysis-services/schema-rowsets/ole-db/ole-db-schema-rowsets.md)|Descrive i set di righe dello schema OLE DB supportati dal provider XMLA.|  
|[OLE DB per OLAP i rowset dello Schema](../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)|Descrive i set di righe dello schema OLE DB per OLAP supportati dal provider XMLA.|  
|[Set di righe dello Schema di Data Mining](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)|Descrive i set di righe dello schema di data mining supportati dal provider XMLA.|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai dati di modello multidimensionale &#40; Analysis Services - dati multidimensionali &#41;](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [Usare dinamica viste a Gestione &#40; viste a gestione dinamica &#41; per monitorare Analysis Services](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
