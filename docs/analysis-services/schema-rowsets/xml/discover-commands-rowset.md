---
title: Set di righe DISCOVER_COMMANDS | Documenti Microsoft
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_COMMANDS rowset
ms.assetid: d228f265-05d9-4d2c-a622-44c73eab7a71
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 49d95852f838c67a34e175ed160c6abdad93bd61
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discovercommands-rowset"></a>Set di righe DISCOVER_COMMANDS
  Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative all'ultimo comando eseguito o attualmente in esecuzione nelle connessioni aperte nel server.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_COMMANDS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|Sì|ID della sessione.|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Numero di comandi eseguito dopo l'avvio della sessione.|  
|**COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora in cui è stato avviato l'ultimo comando espresse come ora UTC del server.|  
|**COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**||Tempo trascorso, in millisecondi, dopo l'avvio del comando.|  
|**COMMAND_CPU_TIME_MS**|**DBTYPE_I8**||Tempo di CPU, in millisecondi, utilizzato dal comando dopo l'avvio dell'esecuzione del comando.|  
|**COMMAND_READS**|**DBTYPE_I8**||Numero accumulato delle letture del disco dopo l'avvio del comando.|  
|**COMMAND_READ_KB**|**DBTYPE_I8**||Valore accumulato dei dati letti dal disco, in KB, dopo l'avvio del comando.|  
|**COMMAND_WRITES**|**DBTYPE_I8**||Numero accumulato delle scritture nel disco dopo l'avvio del comando.|  
|**COMMAND_WRITE_KB**|**DBTYPE_I8**||Valore accumulato dei dati scritti nel disco, in KB, dopo l'avvio del comando.|  
|**COMMAND_TEXT**|**DBTYPE_WSTR**||Testo del comando.|  
|**COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è terminata l'esecuzione del comando.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd34-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Comandi|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

