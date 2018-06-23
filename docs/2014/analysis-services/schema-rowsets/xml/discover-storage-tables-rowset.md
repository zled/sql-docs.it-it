---
title: Set di righe DISCOVER_STORAGE_TABLES | Documenti Microsoft
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
ms.assetid: 13df6f10-8efe-4fe9-83a6-96d108809ed1
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ae51d176ecef04060c58be629b72fe867cd51960
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36069021"
---
# <a name="discoverstoragetables-rowset"></a>Set di righe DISCOVER_STORAGE_TABLES
  Consente al client di determinare le tabelle incluse in un database di Analysis Services in esecuzione in modalità tabulare o SharePoint.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_STORAGE_TABLES` set di righe contiene le colonne seguenti.  
  
|**Nome colonna**|**Indicatore del tipo**|**Length**|**Descrizione**|  
|---------------------|------------------------|----------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`||Viene specificato il nome del database contenente le tabelle.<br /><br /> Il `DISCOVER_STORAGE_TABLES` set di righe può essere limitato tramite questa colonna. Se per limitare il set di righe non viene utilizzata questa colonna, viene utilizzato il database corrente.|  
|`CUBE_NAME`|`DBTYPE_WSTR`||Viene specificato il cubo o il modello contenente le tabelle.<br /><br /> Il `DISCOVER_STORAGE_TABLES` set di righe può essere limitato tramite questa colonna.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`||Nome del gruppo di misure.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`||Nome della partizione.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nome della dimensione.|  
|`TABLE_ID`|`DBTYPE_WSTR`||ID della tabella utilizzata per archiviare gli attributi della tabella.|  
|`TABLE_PARTITIONS_COUNT`|`DBTYPE_ WSTR`||Conteggio della partizione della tabella.|  
|`HINT_TABLE_TYPE`|`DBTYPE_ WSTR`||Hint del tipo di tabella.|  
|`ROWS_COUNT`|`DBTYPE_UI4`||Numero di righe nella partizione.|  
|`RIVIOLATION_COUNT`|`DBTYPE_UI4`||Numero di righe con violazioni di integrità referenziale.|  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_STORAGE_TABLES` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|**Nome colonna**|**Indicatore del tipo**|**Stato della restrizione**|  
|---------------------|------------------------|---------------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Facoltativo.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Facoltativo|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Facoltativo|  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene restituito un elenco delle tabelle di archiviazione e il numero di righe in ognuna, dal database predefinito nella connessione corrente.  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di Analysis Services](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  