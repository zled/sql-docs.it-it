---
title: Set di righe DISCOVER_JOBS | Microsoft Docs
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
- DISCOVER_JOBS rowset
ms.assetid: b4d83bb6-aed3-4513-b516-cefadf95dad2
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a23a3e3dae0a03bf31a7b73b8cb505e834cff27
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246061"
---
# <a name="discoverjobs-rowset"></a>Set di righe DISCOVER_JOBS
  Fornisce informazioni sui processi attivi in esecuzione nel server. Un processo fa parte di un comando che esegue un'attività specifica per conto del comando.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_JOBS` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`JOB_CREATION_TIME`|`DBTYPE_DBTIMESTAMP`||Data e ora UTC del server in cui è stato creato il processo.|  
|`JOB_DESCRIPTION`|`DBTYPE_WSTR`||Descrizione del processo assegnata dal servizio del server.|  
|`JOB_EXECUTION_TIME_MS`|`DBTYPE_I8`||Tempo di attività, in millisecondi, del processo.|  
|`JOB_ID`|`DBTYPE_I4`||Identificatore univoco del processo.|  
|`JOB_START_TIME`|`DBTYPE_DBTIMESTAMP`||Data e ora UTC del server in cui è stato avviato il processo.|  
|`JOB_THREADPOOL_ID`|`DBTYPE_I4`||Pool di thread dal quale è stato avviato il processo corrente.|  
|`JOB_TOTAL_TIME_MS`|`DBTYPE_I8`||Tempo trascorso, in millisecondi, dopo l'avvio del processo.|  
|`SPID`|`DBTYPE_I4`||ID della sessione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_JOBS` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|Facoltativo.|  
|JOB_ID|DBTYPE_I4|Facoltativo.|  
|JOB_DESCRIPTION|DBTYPE_WSTR|Facoltativo.|  
|JOB_THREADPOOL_ID|DBTYPE_I4|Facoltativo.|  
|JOB_MIN TOTAL_TIME_MS|DBTYPE_I8|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
