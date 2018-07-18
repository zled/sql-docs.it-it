---
title: Set di righe DISCOVER_COMMAND_OBJECTS | Microsoft Docs
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
helpviewer_keywords:
- DISCOVER_COMMAND_OBJECTS rowset
ms.assetid: 325114ee-3a50-4504-9782-dbf7c1a44778
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 78970be3b1ed127ad25e4c27fcf81044b1eb9dca
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37261197"
---
# <a name="discovercommandobjects-rowset"></a>Set di righe DISCOVER_COMMAND_OBJECTS
  Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative agli oggetti utilizzati dal comando a cui si fa riferimento.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_COMMAND_OBJECTS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`SESSION_SPID`|`DBTYPE_I4`|Sì|ID della sessione.|  
|`SESSION_ID`|`DBTYPE_WSTR`|Sì|Identificatore univoco della sessione espresso come GUID.|  
|`SESSION_COMMAND_COUNT`|`DBTYPE_I4`||Numero di sequenza del comando.|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`|Sì|Percorso dell'elemento padre dell'oggetto corrente.|  
|`OBJECT_ID`|`DBTYPE_WSTR`|Sì|ID dell'oggetto come definito al momento della creazione.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Numero di versione dei metadati dell'oggetto. Questo numero cambia ad ogni modifica dell'oggetto.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Numero di derivazione dei dati nell'oggetto. Questo numero aumenta ad ogni elaborazione dell'oggetto.|  
|`OBJECT_CPU_TIME_MS`|`DBTYPE_I8`||Tempo di CPU, in millisecondi, utilizzato dall'oggetto dopo l'avvio del comando.|  
|`OBJECT_READ_KB`|`DBTYPE_I8`||Valore accumulato dei dati letti dall'oggetto, in KB, dopo l'avvio del comando.|  
|`OBJECT_READS`|`DBTYPE_I8`||Numero accumulato delle operazioni di lettura eseguite dall'oggetto dopo l'avvio del comando.|  
|`OBJECT_WRITE_KB`|`DBTYPE_I8`||Valore accumulato dei dati scritti dall'oggetto, in KB, dopo l'avvio del comando.|  
|`OBJECT_WRITES`|`DBTYPE_I8`||Numero accumulato delle operazioni di scrittura eseguite dall'oggetto dopo l'avvio del comando.|  
|`OBJECT_ROWS_RETURNED`|`DBTYPE_I8`||Numero di righe restituite dall'oggetto al chiamante dopo l'avvio del comando.|  
|`OBJECT_ROWS_SCANNED`|`DBTYPE_I8`||Numero di righe sottoposte ad analisi dall'oggetto dopo l'avvio del comando.|  
  
 Questo set di righe dello schema non è ordinato.  
  
> [!IMPORTANT]  
>  Il set di righe dello schema DISCOVER_COMMAND_OBJECTS non segnala l'attività tramite le query DMV.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd35-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
