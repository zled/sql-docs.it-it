---
title: Set di righe DISCOVER_TRACES | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7b3c8428b34a72f16986044db1652b9907384b07
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157242"
---
# <a name="discovertraces-rowset"></a>Set di righe DISCOVER_TRACES
  Vengono fornite informazioni sulle tracce attualmente attive nel server.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_TRACES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|`TraceID`|`DBTYPE_WSTR`|ID della traccia.|  
|`TraceName`|`DBTYPE_WSTR`|Nome della traccia.|  
|`LogFileName`|`DBTYPE_WSTR`|Nome del file di log di traccia.|  
|`LogFileSize`|`DBTYPE_I4`|Dimensioni del file di log di traccia.|  
|`LogFileRollover`|`DBTYPE_BOOL`|Se true, indica che il file di log deve essere sottoposto a rollover; in caso contrario false.|  
|`AutoRestart`|`DBTYPE_BOOL`|Se true, indica che l'opzione di riavvio automatico è abilitata; in caso contrario false.|  
|`CreationTime`|`DBTYPE_TIME`|Data e ora di creazione della traccia.|  
|`StopTime`|`DBTYPE_TIME`|Data e ora di arresto di una traccia.|  
|`Type`|`PF_DBTYPE_WSTR`|Tipo di traccia.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_TRACES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|`DBTYPE_I4`|Facoltativo.|  
|`Type`|WSTR|Facoltativo.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRACES|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  