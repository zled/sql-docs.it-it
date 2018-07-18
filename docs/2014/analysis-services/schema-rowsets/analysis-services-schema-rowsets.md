---
title: I set di righe dello Schema di Analysis Services | Microsoft Docs
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
topic_type:
- apiref
- apinav
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
caps.latest.revision: 31
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d01770593787032d96ab869dd59cd40658eca4b0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153232"
---
# <a name="analysis-services-schema-rowsets"></a>Set di righe dello schema di Analysis Services
  I set di righe dello schema sono tabelle predefinite che contengono informazioni sugli oggetti di Analysis Services e sullo stato del server, inclusi schema del database, processi, sessioni attive e connessioni in esecuzione nel server. È possibile eseguire una query sulle tabelle del set di righe dello schema in una finestra di script XML/A in SQL Server Management Studio, eseguire una query DMV su un set di righe dello schema o creare un'applicazione personalizzata contenente informazioni sul set di righe dello schema (ad esempio un'applicazione per la creazione di report che recupera l'elenco di dimensioni disponibili che possono essere utilizzate per creare un report).  
  
> [!NOTE]  
>  Se si usa i set di righe dello schema in XML/A uno script, le informazioni restituite nel *risultato* parametro delle [Discover](../xmla/xml-elements-methods-discover.md) metodo è strutturato in base i layout delle colonne dei set di righe descritti in questo sezione. Il provider [!INCLUDE[msCoName](../../includes/msconame-md.md)] XML for Analysis (XMLA) supporta i set di righe richiesti dalla specifica XML for Analysis. Il provider XMLA supporta inoltre alcuni dei set di righe dello schema standard per i provider delle origini dati OLE DB, OLE DB per OLAP e OLE DB per Data mining. I set di righe supportati sono descritti negli argomenti seguenti.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[XML per set di righe dello schema di analisi](xml/xml-for-analysis-schema-rowsets.md)|Descrive i set di righe XMLA supportati dal provider XMLA.|  
|[Set di righe dello schema OLE DB](ole-db/ole-db-schema-rowsets.md)|Descrive i set di righe dello schema OLE DB supportati dal provider XMLA.|  
|[Set di righe dello schema OLE DB per OLAP](ole-db-olap/ole-db-for-olap-schema-rowsets.md)|Descrive i set di righe dello schema OLE DB per OLAP supportati dal provider XMLA.|  
|[Set di righe dello schema di data mining](data-mining/data-mining-schema-rowsets.md)|Descrive i set di righe dello schema di data mining supportati dal provider XMLA.|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai dati di modelli multidimensionali &#40;Analysis Services - dati multidimensionali&#41;](../multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)   
 [Usare le viste a gestione dinamica &#40;viste a gestione dinamica&#41; per monitorare Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  
