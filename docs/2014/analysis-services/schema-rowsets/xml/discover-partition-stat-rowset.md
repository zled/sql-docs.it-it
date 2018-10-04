---
title: Set di righe DISCOVER_PARTITION_STAT | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 20d339e2-f47f-437f-94d5-5b00b400356a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 749756c55a305997d49ae165b86e71a1fc756be7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129751"
---
# <a name="discoverpartitionstat-rowset"></a>Set di righe DISCOVER_PARTITION_STAT
  Restituisce statistiche sulle aggregazioni in una partizione specifica.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_PARTITION_STAT` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome del database che contiene la dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome del cubo o del modello tabulare contenente la partizione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome di un gruppo di misure nella dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome di una partizione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`AGGREGATION_NAME`|`DBTYPE_WSTR`||Nome dell'aggregazione.|  
|`AGGREGATION_SIZE`|`DBTYPE_I8`||Dimensione dell'aggregazione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd8f-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionStat|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
