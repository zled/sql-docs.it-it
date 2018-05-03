---
title: Set di righe DISCOVER_LOCATIONS | Documenti Microsoft
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
ms.assetid: 6d3a1171-8e4d-4022-ade0-b785cf795d70
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b58cba508faeb566f1ddb5f19bf24ef19d1e8d95
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="discoverlocations-rowset"></a>Set di righe DISCOVER_LOCATIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Restituisce informazioni sul contenuto di un file di backup. È necessario disporre dell'autorizzazione di accesso al percorso del file di backup.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_LOCATIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Obbligatorio, vedere sotto.|Posizione del file di backup.|  
|**LOCATION_PARTITION_OBJECTPATH**|**DBTYPE_WSTR**||Percorso della partizione relativo alla cartella di dati,|  
|**LOCATION_PARTITION_DATASOURCEID**|**DBTYPE_WSTR**||ID dell'origine dati utilizzato per l'elaborazione della partizione.|  
|**LOCATION_PARTITION_DATASOURCENAME**|**DBTYPE_WSTR**||Nome dell'origine dati utilizzata per l'elaborazione.|  
|**LOCATION_PARTITION_NAME**|**DBTYPE_WSTR**||Nome della partizione.|  
|**LOCATION_PARTITION_SIZE**|**DBTYPE_WSTR**||Dimensioni approssimate della partizione.|  
|**LOCATION_CONNECTION_STRING**|**DBTYPE_WSTR**||Stringa di connessione per l'origine dati utilizzata nell'elaborazione.|  
|**LOCATION_PARTITION_FOLDER**|**DBTYPE_WSTR**||Posizione originale di questa partizione quando il file di backup è stato prodotto.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_LOCATIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|Required|  
|**LOCATION_PASSWORD PF_DBTYPE**|**DBTYPE_WSTR**|Obbligatorio se è stato specificato durante il backup. Questa restrizione non viene utilizzata per limitare le righe restituite, ma per fornire la password per accedere alla posizione.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Percorsi|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
