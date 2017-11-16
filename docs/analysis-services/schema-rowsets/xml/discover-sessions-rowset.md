---
title: Set di righe DISCOVER_SESSIONS | Documenti Microsoft
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_SESSIONS rowset
ms.assetid: 47a79542-3142-4e62-a66f-6c4dbfe0f5c0
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 79aeb0bedd96eb02138c424f4e381115ae47d8b1
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="discoversessions-rowset"></a>Set di righe DISCOVER_SESSIONS
  Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative alle sessioni attualmente aperte nel server.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_SESSIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Numero di comandi di cui è stata avviata l'esecuzione dopo l'inizio della sessione.|  
|**SESSION_CONNECTION_ID**|**DBTYPE_I4**||Identificatore di connessione per la sessione.|  
|**SESSION_CPU_TIME_MS**|**DBTYPE_UI8**||Tempo di CPU, in millisecondi, utilizzato da tutte le richieste dopo l'inizio della sessione.|  
|**SESSION_CURRENT_DATABASE**|**DBTYPE_WSTR**||Nome del database utilizzato dal comando attualmente eseguito o del database utilizzato dall'ultimo comando eseguito.|  
|**SESSION_ELAPSED_TIME_MS**|**DBTYPE_UI8**||Tempo trascorso, in millisecondi, dopo l'avvio della sessione.|  
|**SESSION_ID**|**DBTYPE_WSTR**||Identificatore univoco della sessione espresso come GUID.|  
|**SESSION_IDLE_TIME_MS**|**DBTYPE_UI8**||Tempo di inattività, in millisecondi, dopo l'avvio della sessione.|  
|**SESSION_LAST_COMMAND**|**DBTYPE_WSTR**||Il testo del comando attualmente in esecuzione o dell'ultimo comando eseguito.|  
|**SESSION_LAST_COMMAND_CPU_TIME_MS**|**DBTYPE_UI8**||Tempo di CPU, espresso in millisecondi, utilizzato da **SESSION_LAST_COMMAND**.|  
|**SESSION_LAST_COMMAND_ELAPSED_TIME_MS**|**DBTYPE_UI8**||Il tempo trascorso, espresso in millisecondi, dopo l'avvio di **SESSION_LAST_COMMAND**.|  
|**SESSION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||L'ora UTC del server in cui è terminata l'esecuzione dell'ultimo comando.|  
|**SESSION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||L'ora UTC del server in cui è iniziata l'esecuzione dell'ultimo comando.|  
|**SESSION_PROPERTIES**|**DBTYPE_WSTR**||Riservato per utilizzi futuri.|  
|**SESSION_READ_KB**|**DBTYPE_UI8**||Valore accumulato dei dati letti dal disco, in KB, dopo l'avvio della sessione.|  
|**SESSION_READS**|**DBTYPE_UI8**||Numero accumulato delle letture del disco dopo l'avvio della sessione.|  
|**SESSION_SPID**|**DBTYPE_I4**||ID della sessione.|  
|**SESSION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora di avvio della sessione espresse come ora UTC del server.|  
|**SESSION_STATUS**|**DBTYPE_I4**||Stato di attività della sessione.<br /><br /> 0 indica "Inattivo", ovvero nessuna attività in corso.<br /><br /> 1 indica "Attivo", ovvero la sessione sta eseguendo alcune attività richieste.<br /><br /> 2 indica "Bloccato", ovvero la sessione è in attesa di risorse per continuare a eseguire l'attività sospesa.<br /><br /> 3 indica "Annullato": la sessione è stata contrassegnata come annullata.|  
|**SESSION_USED_MEMORY SI**|**DBTYPE_I4**||Dimensione corrente della memoria, in KB, utilizzata dalla sessione. Il valore restituito è l'utilizzo di RAM da parte di SPID, senza distinzione tra la memoria compattabile e quella non compattabile. A differenza di altre DMV da cui viene fornito un report sull'utilizzo della memoria, in DISCOVER_SESSIONS l'utilizzo della memoria non viene suddiviso per categorie.<br /><br /> Si noti che in SESSION_USED_MEMORY si tende a fornire un report di utilizzo effettivo della memoria inferiore poiché vengono esclusi gli oggetti condivisi tra più sessioni.  Nel calcolo della memoria vengono rappresentati solo gli oggetti univoci della sessione.|  
|**SESSION_USER_NAME**|**DBTYPE_WSTR**||Nome utente della sessione.|  
|**SESSION_WRITE_KB**|**DBTYPE_UI8**||Valore accumulato dei dati scritti nel disco, in KB, dopo l'avvio della sessione.|  
|**SESSION_WRITES**|**DBTYPE_UI8**||Numero accumulato delle scritture nel disco dopo l'avvio della sessione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_SESSIONS** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|SESSION_ID|DBTYPE_WSTR|Facoltativa.|  
|SESSION_SPID|DBTYPE_I4|Facoltativa.|  
|SESSION_CONNECTION_ID|DBTYPE_I4|Facoltativa.|  
|SESSION_USER_NAME|DBTYPE_WSTR|Facoltativa.|  
|SESSION_CURRENT_DATABASE|DBTYPE_WSTR|Facoltativa.|  
|SESSION_ELAPSED_TIME_MS|DBTYPE_UI8|Facoltativa.|  
|SESSION_CPU_TIME_MS|DBTYPE_UI8|Facoltativa.|  
|SESSION_IDLE_TIME_MS|DBTYPE_UI8|Facoltativa.|  
|SESSION_STATUS|DBTYPE_I4|Facoltativa.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

