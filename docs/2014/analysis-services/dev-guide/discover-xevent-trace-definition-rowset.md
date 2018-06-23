---
title: Set di righe DISCOVER_XEVENT_TRACE_DEFINITION | Documenti Microsoft
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
ms.assetid: e1ce2d2d-f994-4318-801a-ee0385aecd84
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2994ce526ff0f8035d16485bf99b146e2366389e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067289"
---
# <a name="discoverxeventtracedefinition-rowset"></a>Set di righe DISCOVER_XEVENT_TRACE_DEFINITION
  Vengono fornite informazioni sulle tracce XEvent attualmente attive nel server.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_XEVENT_TRACE_DEFINITION` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||Definizione XML della traccia XEvent.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd1c-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_XEVENT_TRACE_DEFINITION|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i set di righe dello Schema](../schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)   
 [Utilizzare eventi estesi di SQL Server &#40;XEvent&#41; per monitorare Analysis Services](../instances/monitor-analysis-services-with-sql-server-extended-events.md)   
 [Utilizzare viste a gestione dinamica &#40;viste a gestione dinamica&#41; per monitorare Analysis Services](../instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  