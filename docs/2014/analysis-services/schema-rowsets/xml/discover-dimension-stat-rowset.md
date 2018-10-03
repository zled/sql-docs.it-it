---
title: Set di righe DISCOVER_DIMENSION_STAT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 639f8cd7-3b43-40d5-8b84-552daf60d484
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 39ae0bed8c0e0ff7eb272062b79b870dfb31157e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48094981"
---
# <a name="discoverdimensionstat-rowset"></a>Set di righe DISCOVER_DIMENSION_STAT
  Fornisce informazioni su una dimensione, incluso il nome del database che la contiene, il nome della dimensione, i relativi attributi e un conteggio dei membri per ogni attributo. In un modello tabulare corrisponde alle colonne di una tabella e al numero di valori in ogni colonna.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_DIMENSION_STAT` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome del database che contiene la dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`|Obbligatorio|Nome della dimensione.<br /><br /> Questa colonna è obbligatoria nell'elenco di restrizioni.|  
|`ATTRIBUTE_NAME`|`DBTYPE_WSTR`||Nome di un attributo nella dimensione.|  
|`ATTRIBUTE_COUNT`|`DBTYPE_I8`||Conteggio dei valori dell'attributo denominato. Per un modello tabulare il valore corrisponde sempre al numero di righe nella tabella.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd90-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionDimensionStat|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
