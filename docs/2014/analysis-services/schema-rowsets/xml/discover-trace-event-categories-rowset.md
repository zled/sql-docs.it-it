---
title: Set di righe DISCOVER_TRACE_EVENT_CATEGORIES | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 1ad74fd2-4740-469d-85b5-abf0171737fd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4d5771be15bf30b7cd5d478281ff9d859c354f4d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140157"
---
# <a name="discovertraceeventcategories-rowset"></a>Set di righe DISCOVER_TRACE_EVENT_CATEGORIES
  Visualizza l'elenco di categorie di eventi supportate dal provider di traccia.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_TRACE_EVENT_CATEGORIES` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`Data`|`DBTYPE_WSTR`||Contiene una stringa XML codificata con informazioni descrittive sulla categoria di eventi relative al provider di traccia, inclusi il nome della categoria, il tipo e descrizione. Tipo è una stringa che indica il tipo di categoria di eventi. I valori di enumerazione sono i seguenti:<br /><br /> -0 = normale<br />-1 = significative<br />-2 = errore|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd19-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRACE_EVENT_CATEGORIES|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
