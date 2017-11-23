---
title: sp_cycle_errorlog (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cycle_agent_errorlog
- sp_cycle_agent_errorlog_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_cycle_agent_errorlog
ms.assetid: 8aa96182-60b7-4d7b-b2a7-ccce70378c6e
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 59c6136224bc639c4609dd149ade598b3ef80940
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="spcycleagenterrorlog-transact-sql"></a>sp_cycle_agent_errorlog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Chiude il log degli errori corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e rinumera le estensioni del log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, esattamente come quando si riavvia il server. Il nuovo log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent contiene una riga in cui è registrata l'operazione di creazione di un nuovo log.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_cycle_agent_errorlog  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Ogni volta che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente è avviato, corrente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registro errori dell'agente è stato rinominato **SQLAgent. 1**; **SQLAgent. 1** diventa **SQLAgent. 2**, **SQLAgent. 2** diventa **SQLAgent. 3**e così via. **sp_cycle_agent_errorlog** consente di rinumerare il file di log degli errori senza arrestare e riavviare il server.  
  
 È necessario eseguire questa stored procedure dal **msdb** database.  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni di esecuzione **sp_cycle_agent_errorlog** sono limitate ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rinumerato il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_cycle_agent_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_cycle_errorlog &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md)  
  
  
