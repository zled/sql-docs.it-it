---
title: sp_enum_sqlagent_subsystems (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enum_sqlagent_subsystems
- sp_enum_sqlagent_subsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_sqlagent_subsystems
ms.assetid: 019a3c9d-bac3-495b-a70a-2c19f1d2e20e
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ad4a380353dddd0bf17a25952b81220f2f2e6a2d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spenumsqlagentsubsystems-transact-sql"></a>sp_enum_sqlagent_subsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elenca i sottosistemi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_enum_sqlagent_subsystems  
```  
  
## <a name="arguments"></a>Argomenti  
 Nessuno  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**subsystem**|**nvarchar(40)**|Nome del sottosistema.|  
|**description**|**nvarchar(512)**|Descrizione del sottosistema.|  
|**subsystem_dll**|**nvarchar(510)**|Modulo DLL contenente il sottosistema.|  
|**agent_exe**|**nvarchar(510)**|Modulo eseguibile utilizzato dal sottosistema.|  
|**start_entry_point**|**nvarchar(30)**|Procedura richiamata da SQL Server Agent durante l'esecuzione del passaggio del processo.|  
|**event_entry_point**|**nvarchar(30)**|Procedura richiamata da SQL Server Agent durante l'esecuzione del passaggio del processo.|  
|**stop_entry_point**|**nvarchar(30)**|Procedura richiamata da SQL Server Agent durante l'esecuzione del passaggio del processo.|  
|**max_worker_threads**|**int**|Numero massimo di thread avviati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per questo sottosistema.|  
|**subsystem_id**|**int**|Identificatore del sottosistema.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa procedura elenca i sottosistemi disponibili nell'istanza.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono appartenere al ruolo predefinito del database **SQLAgentOperatorRole** nel database **msdb** .  
  
 Per informazioni dettagliate su **SQLAgentOperatorRole**, vedere [SQL Server Agent Fixed Database Roles](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione della sicurezza SQL Server Agent](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
  
