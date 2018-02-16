---
title: Set di righe DISCOVER_PARTITION_STAT | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 20d339e2-f47f-437f-94d5-5b00b400356a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 649475fa5fd1a4e0bb2a6c734f916270ac7f9a64
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="discoverpartitionstat-rowset"></a>Set di righe DISCOVER_PARTITION_STAT
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Restituisce statistiche sulle aggregazioni in una partizione specifica.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_PARTITION_STAT** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|Required|Nome del database che contiene la dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**CUBE_NAME**|**DBTYPE_WSTR**|Required|Nome del cubo o del modello tabulare contenente la partizione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|Required|Nome di un gruppo di misure nella dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|Required|Nome di una partizione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|**AGGREGATION_NAME**|**DBTYPE_WSTR**||Nome dell'aggregazione.|  
|**AGGREGATION_SIZE**|**DBTYPE_I8**||Dimensione dell'aggregazione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd8f-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionStat|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
