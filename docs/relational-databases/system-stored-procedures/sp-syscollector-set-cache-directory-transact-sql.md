---
title: sp_syscollector_set_cache_directory (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_cache_directory_TSQL
- sp_syscollector_set_cache_directory
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_set_cache_directory stored procedure
ms.assetid: df56d5a5-8961-494f-a745-d752ca63805a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 504a7b7c769910fafa8b598c5a3f20714a50dcd6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spsyscollectorsetcachedirectory-transact-sql"></a>sp_syscollector_set_cache_directory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Specifica la directory in cui vengono archiviati i dati raccolti prima di essere caricati nel data warehouse di gestione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syscollector_set_cache_directory [ @cache_directory = ] 'cache_directory'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@cache_directory =** ] **'***cache_directory***'**  
 Directory nel file system in cui i dati raccolti vengono archiviati temporaneamente. *cache_directory* è **nvarchar (255)**, con un valore predefinito null. Se non viene specificato alcun valore, viene utilizzata la directory temporanea predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 È necessario disabilitare l'agente di raccolta dati prima di modificare la configurazione della directory della cache. La stored procedure ha esito negativo se l'agente di raccolta dati è abilitato. Per ulteriori informazioni, vedere [abilitare o disabilitare la raccolta dei dati](../../relational-databases/data-collection/enable-or-disable-data-collection.md), e [gestire raccolta dati](../../relational-databases/data-collection/manage-data-collection.md).  
  
 Nel momento in cui sp_syscollector_set_cache_directory viene eseguita la directory specificata non deve essere esistere. I dati tuttavia non possono essere memorizzati nella cache né caricati in modo corretto fino a quando la directory non viene creata. È consigliabile pertanto creare la directory prima di eseguire questa stored procedure.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire questa procedura, è richiesta l'appartenenza al ruolo predefinito del database dc_admin (con autorizzazione EXECUTE) .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene disabilitato l'agente di raccolta dati, imposta la directory della cache per l'agente di raccolta dati per `D:\tempdata`e quindi Abilita l'agente di raccolta dati.  
  
```sql  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_disable_collector;  
GO  
EXEC dbo.sp_syscollector_set_cache_directory N'D:\tempdata';  
GO  
EXECUTE dbo.sp_syscollector_enable_collector;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [sp_syscollector_set_cache_window &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql.md)  
  
  
