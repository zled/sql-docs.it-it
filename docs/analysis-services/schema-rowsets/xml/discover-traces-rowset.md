---
title: Set di righe DISCOVER_TRACES | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 63bcb03d27abdacf675acd56c95a2dbd49adb362
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34028722"
---
# <a name="discovertraces-rowset"></a>Set di righe DISCOVER_TRACES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
