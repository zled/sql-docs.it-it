---
title: Set di righe DISCOVER_STORAGE_TABLES | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0685808f47364f7e88f82b48540034ef0d0e688a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="discoverstoragetables-rowset"></a>Set di righe DISCOVER_STORAGE_TABLES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Consente al client di determinare le tabelle incluse in un database di Analysis Services in esecuzione in modalità tabulare o SharePoint.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_STORAGE_TABLES** set di righe contiene le colonne seguenti.  
  
|**Nome colonna**|**Indicatore del tipo**|**Length**|**Description**|  
|---------------------|------------------------|----------------|---------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**||Viene specificato il nome del database contenente le tabelle.<br /><br /> Il **DISCOVER_STORAGE_TABLES** righe può essere limitato tramite questa colonna. Se per limitare il set di righe non viene utilizzata questa colonna, viene utilizzato il database corrente.|  
|**CUBE_NAME**|**DBTYPE_WSTR**||Viene specificato il cubo o il modello contenente le tabelle.<br /><br /> Il **DISCOVER_STORAGE_TABLES** righe può essere limitato tramite questa colonna.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**||Nome del gruppo di misure.|  
|**PARTITION_NAME**|**DBTYPE_WSTR**||Nome della partizione.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Nome della dimensione.|  
|**TABLE_ID**|**DBTYPE_WSTR**||ID della tabella utilizzata per archiviare gli attributi della tabella.|  
|**TABLE_PARTITIONS_COUNT**|**DBTYPE WSTR**||Conteggio della partizione della tabella.|  
|**HINT_TABLE_TYPE**|**DBTYPE WSTR**||Hint del tipo di tabella.|  
|**ROWS_COUNT**|**DBTYPE_UI4**||Numero di righe nella partizione.|  
|**RIVIOLATION_COUNT**|**DBTYPE_UI4**||Numero di righe con violazioni di integrità referenziale.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_STORAGE_TABLES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|**Nome colonna**|**Indicatore del tipo**|**Stato della restrizione**|  
|---------------------|------------------------|---------------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Facoltativa.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Facoltativo|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|Facoltativo|  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene restituito un elenco delle tabelle di archiviazione e il numero di righe in ognuna, dal database predefinito nella connessione corrente.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello Schema di Analysis Services](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
