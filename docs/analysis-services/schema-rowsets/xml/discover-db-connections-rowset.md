---
title: Set di righe DISCOVER_DB_CONNECTIONS | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_DB_CONNECTIONS rowset
ms.assetid: 12a51a4e-5f3d-4449-9d94-7836fea1bc8b
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f6c6fbeac76e14dd410ed8dafcb739e5797cc270
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="discoverdbconnections-rowset"></a>Set di righe DISCOVER_DB_CONNECTIONS
  Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle connessioni attualmente aperte dal server a un database.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_DB_CONNECTIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CONNECTION_CATALOG_NAME**|**DBTYPE_WSTR**||Nome del database attualmente connesso.|  
|**CONNECTION_ID**|**DBTYPE_I4**||Numero univoco che identifica la connessione.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**||Tempo di inattività, in millisecondi, dopo l'avvio della connessione.|  
|**CONNECTION_IN_USE**|**DBTYPE_I4**||Indica se la connessione è attiva (1) o inattiva (0).|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è terminata l'esecuzione dell'ultimo comando.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è iniziata l'esecuzione dell'ultimo comando.|  
|**CONNECTION_SERVER_NAME**|**DBTYPE_WSTR**||Nome del server attualmente connesso.|  
|**CONNECTION_SPID**|**DBTYPE_I4**||ID della sessione.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è iniziata la connessione.|  
|**CONNECTION_USAGE_TIME_MS**|**DBTYPE_I8**||Tempo di attività della connessione, in millisecondi, dopo l'avvio della connessione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
> [!IMPORTANT]  
>  Il **DISCOVER_DB_CONNECTIONS** set di righe visualizzerà informazioni solo quando il servizio è connesso alle origini dati relazionali.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_DB_CONNECTIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|Facoltativa.|  
|CONNECTION_IN_USE|DBTYPE_I4|Facoltativa.|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|Facoltativa.|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|Obbligatorio.|  
|CONNECTION_SPID|DBTYPE_I4|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
