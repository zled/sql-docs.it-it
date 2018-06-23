---
title: Set di righe DISCOVER_PARTITION_DIMENSION_STAT | Documenti Microsoft
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
ms.assetid: bf4626b3-4d6b-4795-bb01-df335fb9c09a
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 798fa10d608db06da3a45041df25c11047dc7a7f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063721"
---
# <a name="discoverpartitiondimensionstat-rowset"></a>Set di righe DISCOVER_PARTITION_DIMENSION_STAT
  Restituisce statistiche sulla dimensione associata a una partizione  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_PARTITION_DIMENSION_STAT` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome del database.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`CUBE_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome del cubo o del modello tabulare.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome del gruppo di misure.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome della partizione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||Nome della dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Nome di un attributo nella dimensione.|  
|`ATTRIBUTE_INDEXED`|`DBTYPE_BOOL`||Se true indica che l'attributo viene indicizzato; in caso contrario false.|  
|`ATTRIBUTE_COUNT_MIN`|`DBTYPE_I8`||Conteggio minimo dell'attributo.|  
|`ATTRIBUTE_COUNT_MAX`|`DBTYPE_I8`||Conteggio massimo dell'attributo.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd8e-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  