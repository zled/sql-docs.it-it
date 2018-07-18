---
title: Set di righe DISCOVER_LOCKS | Microsoft Docs
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
- DISCOVER_LOCKS rowset
ms.assetid: dea48167-212c-40b7-a416-434042a1b697
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4458d9dac98fd35d54ff35c0d1d524a92b576ba5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167599"
---
# <a name="discoverlocks-rowset"></a>Set di righe DISCOVER_LOCKS
  Fornisce informazioni sui blocchi correnti presenti nel server.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_LOCKS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`LOCK_CREATION_TIME`|`DBTYPE_DBTIMESTAMP`||L'ora UTC del server al momento della richiesta del blocco.|  
|`LOCK_GRANT_TIME`|`DBTYPE_DBTIMESTAMP`||L'ora UTC del server nel momento in cui è stato concesso il blocco sulla risorsa.|  
|`LOCK_ID`|`DBTYPE_GUID`||Identificatore univoco del blocco espresso come GUID.|  
|`LOCK_OBJECT_ID`|`DBTYPE_WSTR`||Identificatore univoco dell'oggetto bloccato.|  
|`LOCK_STATUS`|`DBTYPE_I4`||Stato del blocco:<br /><br /> 0 indica che il blocco è in attesa di essere applicato all'oggetto.<br /><br /> 1 indica che il blocco è stato concesso.|  
|`LOCK_TRANSACTION_ID`|`DBTYPE_GUID`||Identificatore univoco della transazione espresso come GUID.|  
|`LOCK_TYPE`|`DBTYPE_I4`||Maschera di bit dei tipi di blocco. Per ulteriori informazioni, vedere la sezione Osservazioni di questo argomento.|  
|`SPID`|`DBTYPE_I4`||ID della sessione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_LOCKS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Facoltativo.|  
|LOCK_TRANSACTION_ID|DBTYPE_GUID|Facoltativo.|  
|LOCK_OBJECT_ID|DBTYPE_WSTR|Facoltativo.|  
|LOCK_STATUS|DBTYPE_I4|Facoltativo.|  
|LOCK_TYPE|DBTYPE_I4|Facoltativo.|  
|LOCK_MIN_TOTAL_MS|DBTYPE_I8|Facoltativo.|  
  
## <a name="remarks"></a>Note  
  
## <a name="lock-types"></a>Tipi di blocco  
  
|Nome del blocco|valore|Description|  
|---------------|-----------|-----------------|  
|LOCK_NONE|0x0000000|Nessun blocco.|  
|LOCK_SESSION_LOCK|0x0000001|Sessione inattiva; nessuna interferenza con altri blocchi.|  
|LOCK_READ|0x0000002|Lettura del blocco durante l'elaborazione.|  
|LOCK_WRITE|0x0000004|Scrittura del blocco durante l'elaborazione.|  
|LOCK_COMMIT_READ|0x0000008|Blocco del commit, condiviso.|  
|LOCK_COMMIT_WRITE|0x0000010|Blocco del commit, esclusivo.|  
|LOCK_COMMIT_ABORTABLE|0x0000020|Interruzione all'avanzamento del commit.|  
|LOCK_COMMIT_INPROGRESS|0x0000040|Commit in corso.|  
|LOCK_INVALID|0x0000080|Blocco non valido.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
