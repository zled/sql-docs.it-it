---
title: Set di righe DISCOVER_PARTITION_DIMENSION_STAT | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: fe43b694b8fdeb4128ae1ad2aa9dc137d2bc9d42
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34034512"
---
# <a name="discoverpartitiondimensionstat-rowset"></a>Set di righe DISCOVER_PARTITION_DIMENSION_STAT
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Restituisce statistiche sulla dimensione associata a una partizione  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe **DISCOVER_PARTITION_DIMENSION_STAT** contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Required|Nome del database.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Required|Nome del cubo o del modello tabulare.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Required|Nome del gruppo di misure.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|Required|Nome della partizione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||Nome della dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||Nome di un attributo nella dimensione.|  
|**ATTRIBUTE_INDEXED**|**DBTYPE_BOOL**||Se true indica che l'attributo viene indicizzato; in caso contrario false.|  
|**ATTRIBUTE_COUNT_MIN**|**DBTYPE_I8**||Conteggio minimo dell'attributo.|  
|**ATTRIBUTE_COUNT_MAX**|**DBTYPE_I8**||Conteggio massimo dell'attributo.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd8e-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
