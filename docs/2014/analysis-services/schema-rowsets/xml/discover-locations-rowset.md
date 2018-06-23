---
title: Set di righe DISCOVER_LOCATIONS | Documenti Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6d3a1171-8e4d-4022-ade0-b785cf795d70
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cfcc451a3369a3f15e29381df3d21e7275a90f7f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36158545"
---
# <a name="discoverlocations-rowset"></a>Set di righe DISCOVER_LOCATIONS
  Restituisce informazioni sul contenuto di un file di backup. È necessario disporre dell'autorizzazione di accesso al percorso del file di backup.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_LOCATIONS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`LOCATION_BACKUP_FILE_PATHNAME`|`DBTYPE_WSTR`|Obbligatorio, vedere sotto.|Posizione del file di backup.|  
|`LOCATION_PARTITION_OBJECTPATH`|`DBTYPE_WSTR`||Percorso della partizione relativo alla cartella di dati,|  
|`LOCATION_PARTITION_DATASOURCEID`|`DBTYPE_WSTR`||ID dell'origine dati utilizzato per l'elaborazione della partizione.|  
|`LOCATION_PARTITION_DATASOURCENAME`|`DBTYPE_WSTR`||Nome dell'origine dati utilizzata per l'elaborazione.|  
|`LOCATION_PARTITION_NAME`|`DBTYPE_WSTR`||Nome della partizione.|  
|`LOCATION_PARTITION_SIZE`|`DBTYPE_WSTR`||Dimensioni approssimate della partizione.|  
|`LOCATION_CONNECTION_STRING`|`DBTYPE_WSTR`||Stringa di connessione per l'origine dati utilizzata nell'elaborazione.|  
|`LOCATION_PARTITION_FOLDER`|`DBTYPE_WSTR`||Posizione originale di questa partizione quando il file di backup è stato prodotto.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_LOCATIONS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`LOCATION_BACKUP_FILE_PATHNAME`|`DBTYPE_WSTR`|Obbligatorio|  
|`LOCATION_PASSWORD PF_DBTYPE`|`DBTYPE_WSTR`|Obbligatorio se è stato specificato durante il backup. Questa restrizione non viene utilizzata per limitare le righe restituite, ma per fornire la password per accedere alla posizione.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Percorsi|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  