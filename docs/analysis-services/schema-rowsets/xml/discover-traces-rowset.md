---
title: Set di righe DISCOVER_TRACES | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b48a6756325dc95da634842c5f695378b20319b9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="discovertraces-rowset"></a>Set di righe DISCOVER_TRACES
  Vengono fornite informazioni sulle tracce attualmente attive nel server.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_TRACES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**TraceID**|**DBTYPE_WSTR**|ID della traccia.|  
|**Nome traccia**|**DBTYPE_WSTR**|Nome della traccia.|  
|**LogFileName**|**DBTYPE_WSTR**|Nome del file di log di traccia.|  
|**LogFileSize**|**DBTYPE_I4**|Dimensioni del file di log di traccia.|  
|**LogFileRollover**|**DBTYPE_BOOL**|Se true, indica che il file di log deve essere sottoposto a rollover; in caso contrario false.|  
|**Riavvio automatico**|**DBTYPE_BOOL**|Se true, indica che l'opzione di riavvio automatico è abilitata; in caso contrario false.|  
|**CreationTime**|**DBTYPE_TIME**|Data e ora di creazione della traccia.|  
|**StopTime**|**DBTYPE_TIME**|Data e ora di arresto di una traccia.|  
|**Tipo**|**PF_DBTYPE_WSTR**|Tipo di traccia.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_TRACES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|**DBTYPE_I4**|Facoltativa.|  
|**Tipo**|WSTR|Facoltativa.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRACES|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
