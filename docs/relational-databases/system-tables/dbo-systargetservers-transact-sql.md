---
title: dbo.systargetservers (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.systargetservers_TSQL
- dbo.systargetservers
- systargetservers_TSQL
- systargetservers
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservers system table
ms.assetid: 479d1314-be37-4d19-ac9c-419fc9110e53
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a5f8975f4bbdf2370437efab583f3641f998538c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Registra i server di destinazione integrati nel dominio multiserver specificato.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID del server.|  
|**server_name**|**sysname**|Nome del server.|  
|**location**|**nvarchar(200)**|Posizione del server di destinazione specificato.|  
|**time_zone_adjustment**|**int**|Regolazione del fuso orario in ore rispetto all'ora di Greenwich (GMT).|  
|**enlist_date**|**datetime**|Data e ora in cui il server di destinazione specificato è stato integrato.|  
|**last_poll_date**|**datetime**|Data e ora che il server di destinazione specificato ultimo polling del multiserver **sysdownloadlist** tabella di sistema per i processi da eseguire.|  
|**status**|**int**|Stato del server di destinazione:<br /><br /> **1** = normale<br /><br /> **2** = ripetizione sincronizzazione in sospeso<br /><br /> **4** = Offline sospetto|  
|**local_time_at_last_poll**|**datetime**|Data e ora dell'ultimo polling del server di destinazione per operazioni di processo.|  
|**enlisted_by_nt_user**|**nvarchar(100)**|Nome utente dell'utente che esegue **sp_msx_enlist** nel server di destinazione.|  
|**poll_internal**|**int**|Numero di secondi che deve trascorrere prima che il server di destinazione esegua il polling del server master per individuare nuove istruzioni di download.|  
  
  
