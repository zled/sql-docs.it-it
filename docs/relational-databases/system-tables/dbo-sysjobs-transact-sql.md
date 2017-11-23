---
title: dbo.sysjobs (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysjobs
- sysjobs_TSQL
- dbo.sysjobs
- dbo.sysjobs_TSQL
dev_langs: TSQL
helpviewer_keywords: sysjobs system table
ms.assetid: e244a6a5-54c2-47a6-8039-dd1852b0ae59
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 1fd6e90a9e823e38a83f5b218027e15183ab76ae
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="dbosysjobs-transact-sql"></a>dbo.sysjobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia le informazioni su tutti i processi pianificati da eseguire tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ID univoco del processo.|  
|**originating_server_id**|**int**|ID del server di provenienza del processo.|  
|**name**|**sysname**|Nome del processo|  
|**abilitato**|**tinyint**|Indica se il processo è abilitato per l'esecuzione.|  
|**Descrizione**|**nvarchar(512)**|Descrizione del processo.|  
|**start_step_id**|**int**|ID del passaggio del processo da cui deve iniziare l'esecuzione.|  
|**category_id**|**int**|ID della categoria del processo.|  
|**owner_sid**|**varbinary (85)**|ID di sicurezza (SID) del proprietario del processo.|  
|**notify_level_eventlog**|**int**|**Maschera di bit** che indica in quali circostanze deve essere registrato un evento di notifica nel registro applicazioni di Microsoft Windows:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = al termine del processo (indipendentemente dal risultato del processo)|  
|**notify_level_email**|**int**|Maschera di bit che indica le condizioni per l'invio di un messaggio di posta elettronica di notifica al termine di un processo:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = al termine del processo (indipendentemente dal risultato del processo)|  
|**notify_level_netsend**|**int**|Maschera di bit che indica le condizioni per l'invio di un messaggio in rete al termine di un processo:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = al termine del processo (indipendentemente dal risultato del processo)|  
|**notify_level_page**|**int**|Maschera di bit che indica le condizioni per l'invio di un messaggio su cercapersone al termine di un processo:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = al termine del processo (indipendentemente dal risultato del processo)|  
|**notify_email_operator_id**|**int**|Nome di posta elettronica dell'operatore a cui inviare la notifica.|  
|**notify_netsend_operator_id**|**int**|ID del computer o dell'utente utilizzato quando si invia un messaggio in rete.|  
|**notify_page_operator_id**|**int**|ID del computer o dell'utente utilizzato quando si invia un messaggio su cercapersone.|  
|**possibili**|**int**|**Maschera di bit** che indica in quali circostanze deve eliminare il processo al completamento di un processo:<br /><br /> **0** non = mai<br /><br /> **1** = in caso di esito positivo processo<br /><br /> **2** = in caso di esito negativo del processo<br /><br /> **3** = al termine del processo (indipendentemente dal risultato del processo)|  
|**Date_Created**|**datetime**|Data di creazione del processo.|  
|**date_modified**|**datetime**|Data dell'ultima modifica del processo.|  
|**Version_number**|**int**|Versione del processo.|  
  
  
