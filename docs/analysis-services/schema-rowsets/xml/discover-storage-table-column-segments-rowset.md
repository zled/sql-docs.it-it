---
title: Set di righe DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 3e514715-9fe6-4e6a-accb-4149ffd7e0bf
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8fd3bd96766ad26c21813f137f8f12452932dea7
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>Set di righe DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS
  Vengono fornite informazioni a livello di colonna e segmento sulle tabelle di archiviazione utilizzate da un database di Analysis Services in esecuzione in tabulare o [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] modalità. Questo set di righe viene utilizzato principalmente per la risoluzione dei problemi e l'analisi.  
  
 **Si applica a:** i modelli tabulari  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS** set di righe contiene le colonne seguenti.  
  
|**Nome colonna**|**Indicatore del tipo**|**Restrizione**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Sì|Specifica il database tabulare.<br /><br /> Il **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS** righe può essere limitato tramite questa colonna. Se omesso, viene utilizzato il database corrente.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Sì|Il nome del modello.<br /><br /> Il **DISCOVER_STORAGE_TABLES** righe può essere limitato tramite questa colonna.|  
|**NOME_GRUPPO_MISURE**|**DBTYPE_WSTR**|Sì|Nome del gruppo di misure.|  
|**NOME_PARTIZIONE**|**DBTYPE_WSTR**|Sì|Nome della partizione.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Nome della dimensione.|  
|**TABLE_ID**|**DBTYPE_WSTR**||ID interno del segmento di tabella.|  
|**COLUMN_ID**|**DBTYPE_WSTR**||ID interno della colonna.|  
|**NUMERO SEGMENTO**|**DBTYPE_I8**||Numero ordinale del segmento di tabella.|  
|**TABLE_PARTTION_NUMBER**|**DBTYPE_I8**||Numero ordinale della partizione.|  
|**RECORDS_COUNT**|**DBTYPE_I8**||Numero di record nella partizione.|  
|**ALLOCATED_SIZE**|**DBTYPE_UI8**||Dimensioni in byte allocate al segmento di colonna.|  
|**USED_SIZE**|**DBTYPE_UI8**||Dimensioni in byte utilizzate dal segmento di colonna.|  
|**COMPRESSION_TYPE**|**DBTYPE_WSTR**||Tipo di compressione applicato al segmento di colonna. Questo valore è progettato solo per uso interno e per il supporto clienti. Microsoft non pubblica valori validi o descrizioni per questa colonna.|  
|**BITS_COUNT**|**DBTYPE_I8**||Conteggio di bit.|  
|**BOOKMARK_BITS_COUNT**|**DBTYPE_I8**||Conteggio di bit segnalibro.|  
|**VERTIPAQ_STATE**|**DBTYPE_WSTR**||Stato della compressione VertiPaq per questo segmento di colonna. I possibili valori sono i seguenti:<br /><br /> SKIPPED. La compressione VertiPaq è stata ignorata.<br /><br /> COMPLETED. La compressione VertiPaq è stata completata.<br /><br /> TIMEBOXED. La compressione VertiPaq è stata sottoposta a timebox.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
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
 [Set di righe dello Schema di Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  

