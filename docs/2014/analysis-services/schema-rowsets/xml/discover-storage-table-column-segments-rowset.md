---
title: Set di righe DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 3e514715-9fe6-4e6a-accb-4149ffd7e0bf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 111aa44a99c59fdc4bb9953903e2827c79b54104
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133483"
---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>Set di righe DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS
  Fornisce informazioni a livello di colonna e di segmento sulle tabelle di archiviazione utilizzate da un database di Analysis Services in esecuzione in modalità tabulare o PowerPivot. Questo set di righe viene utilizzato principalmente per la risoluzione dei problemi e l'analisi.  
  
 **Si applica a:** i modelli tabulari  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS` set di righe contiene le colonne seguenti.  
  
|**Nome colonna**|**Indicatore del tipo**|**Restrizione**|**Descrizione**|  
|---------------------|------------------------|---------------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Sì|Specifica il database tabulare.<br /><br /> Il `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS` righe può essere limitato tramite questa colonna. Se omesso, viene utilizzato il database corrente.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Sì|Il nome del modello.<br /><br /> Il `DISCOVER_STORAGE_TABLES` righe può essere limitato tramite questa colonna.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Sì|Nome del gruppo di misure.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Sì|Nome della partizione.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nome della dimensione.|  
|`TABLE_ID`|`DBTYPE_WSTR`||ID interno del segmento di tabella.|  
|`COLUMN_ID`|`DBTYPE_WSTR`||ID interno della colonna.|  
|`SEGMENT _NUMBER`|`DBTYPE_I8`||Numero ordinale del segmento di tabella.|  
|`TABLE_PARTTION_NUMBER`|`DBTYPE_I8`||Numero ordinale della partizione.|  
|`RECORDS_COUNT`|`DBTYPE_I8`||Numero di record nella partizione.|  
|`ALLOCATED_SIZE`|`DBTYPE_UI8`||Dimensioni in byte allocate al segmento di colonna.|  
|`USED_SIZE`|`DBTYPE_UI8`||Dimensioni in byte utilizzate dal segmento di colonna.|  
|`COMPRESSION_TYPE`|`DBTYPE_WSTR`||Tipo di compressione applicato al segmento di colonna. Questo valore è progettato solo per uso interno e per il supporto clienti. Microsoft non pubblica valori validi o descrizioni per questa colonna.|  
|`BITS_COUNT`|`DBTYPE_I8`||Conteggio di bit.|  
|`BOOKMARK_BITS_COUNT`|`DBTYPE_I8`||Conteggio di bit segnalibro.|  
|`VERTIPAQ_STATE`|`DBTYPE_WSTR`||Stato della compressione VertiPaq per questo segmento di colonna. I possibili valori sono i seguenti:<br /><br /> -SKIPPED la compressione VertiPaq è stata ignorata.<br />-COMPLETATA, la compressione VertiPaq è stata completata.<br />La compressione - TIMEBOXED il VertiPaq è stata a timebox.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd45-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageSegments|  
  
## <a name="example"></a>Esempio  
 Tramite la query seguente vengono restituiti i segmenti della tabella di archiviazione associati all'attributo del modello LastName, nel database corrente.  
  
```  
SELECT DISTINCT TABLE_ID, COLUMN_ID   
FROM $system.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS  
WHERE COLUMN_ID = 'LastName'  
ORDER BY TABLE_ID  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di Analysis Services](../analysis-services-schema-rowsets.md)  
  
  
