---
title: Set di righe DISCOVER_STORAGE_TABLE_COLUMNS | Microsoft Docs
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
ms.assetid: 24abb88e-33a9-4ae2-829d-cdef0ff22ec1
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e480f60aa857506a1d192452b299cede3f7161e5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37153152"
---
# <a name="discoverstoragetablecolumns-rowset"></a>Set di righe DISCOVER_STORAGE_TABLE_COLUMNS
  Vengono fornite informazioni a livello di colonna sulle tabelle di archiviazione utilizzate da un database di Analysis Services in esecuzione in modalità SharePoint o tabulare.  
  
 **Si applica a:** i modelli tabulari  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_STORAGE_TABLE_COLUMNS` set di righe contiene le colonne seguenti.  
  
|**Nome colonna**|**Indicatore del tipo**|**Restrizione**|**Descrizione**|  
|---------------------|------------------------|---------------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Sì|Viene specificato il nome del database contenente le tabelle. Se omesso, viene utilizzato il database corrente.<br /><br /> Il `DISCOVER_STORAGE_TABLE_COLUMNS` righe può essere limitato tramite questa colonna.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Sì|Viene specificato il cubo o il modello contenente le tabelle.<br /><br /> Il `DISCOVER_STORAGE_TABLES` righe può essere limitato tramite questa colonna.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Sì|Nome del gruppo di misure.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nome della dimensione.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Nome dell'attributo.|  
|`TABLE_ID`|`DBTYPE_WSTR`||ID della tabella.|  
|`COLUMN_ID`|`DBTYPE_ WSTR`||ID della colonna. L'ID della colonna è interno al motore di analisi in memoria xVelocity (VertiPaq) ed è solo informativo.|  
|`COLUMN_TYPE`|`DBTYPE_WSTR`||Tipo di colonna. Il tipo di colonna è interno al motore di analisi in memoria xVelocity (VertiPaq) ed è solo informativo.<br /><br /> -BASIC_DATA<br />-HIERARCHY_DATAID_TO_POSITION<br />-HIERARCHY_POSITION_TO_DATAID<br />-LA RELAZIONE|  
|`COLUMN_ENCODING`|`DBTYPE_UI8`||Integer che rappresenta il tipo di codifica utilizzato per i dati della colonna.<br /><br /> -   **0**, utilizzato con `COLUMN_TYPE`: HIERARCHY_DATAID_TO_POSITION, HIERARCHY_POSITION_TO_DATAID, RELATIONSHIP<br />-   **1**, utilizzato con `COLUMN_TYPE`: BASIC_DATA<br />-   **2**, utilizzato con `COLUMN_TYPE`: BASIC_DATA|  
|`DATATYPE`|`DBTYPE_WSTR`||Tipo di dati della colonna. Dispone dei seguenti valori possibili:<br /><br /> -DBTYPE_BOOL<br />-DBTYPE_CY<br />-DBTYPE_DATE<br />-DBTYPE_I4<br />-DBTYPE_I8<br />-DBTYPE_R8<br />-DBTYPE_WSTR<br />-N/D|  
|`ISKEY`|`DBTYPE_BOOL`||`True` se la colonna viene utilizzata come chiave primaria o esterna; in caso contrario, `false`.|  
|`ISUNIQUE`|`DBTYPE_BOOL`||`True` se i valori nella colonna sono univoci; in caso contrario, `false`.|  
|`ISNULLABLE`|`DBTYPE_BOOL`||`True` se la colonna ammette valori Null; in caso contrario, `false`.|  
|`ISROWNUMBER`|`DBTYPE_BOOL`||`True` se la colonna è una colonna del numero di riga. Colonne del numero di riga per uso interno da parte del motore di analisi in memoria xVelocity.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd44-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageTableColumns|  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene utilizzata una query DMV per restituire il set di risultati.  
  
```  
SELECT *  
FROM $System.DISCOVER_STORAGE_TABLE_COLUMNS  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Set di righe dello schema di Analysis Services](../analysis-services-schema-rowsets.md)  
  
  
