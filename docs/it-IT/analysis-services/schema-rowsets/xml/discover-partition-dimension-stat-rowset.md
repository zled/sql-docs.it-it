---
title: Set di righe DISCOVER_PARTITION_DIMENSION_STAT | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: bf4626b3-4d6b-4795-bb01-df335fb9c09a
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 14ec5f539005bd736406b82f0c8eac1f49a41259
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
  
