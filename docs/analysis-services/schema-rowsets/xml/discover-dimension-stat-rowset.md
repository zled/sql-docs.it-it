---
title: Set di righe DISCOVER_DIMENSION_STAT | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e70810469afe11b6f63c21a9c040e1a3bd32549
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="discoverdimensionstat-rowset"></a>Set di righe DISCOVER_DIMENSION_STAT
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fornisce informazioni su una dimensione, incluso il nome del database che la contiene, il nome della dimensione, i relativi attributi e un conteggio dei membri per ogni attributo. In un modello tabulare corrisponde alle colonne di una tabella e al numero di valori in ogni colonna.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_DIMENSION_STAT** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Required|Nome del database che contiene la dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**|Required|Nome della dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||Nome di un attributo nella dimensione.|  
|**ATTRIBUTE_COUNT**|**DBTYPE_I8**||Conteggio dei valori dell'attributo denominato. Per un modello tabulare il valore corrisponde sempre al numero di righe nella tabella.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd90-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
