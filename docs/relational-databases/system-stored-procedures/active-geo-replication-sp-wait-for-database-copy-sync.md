---
title: sp_wait_for_database_copy_sync (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: 
ms.prod_service: database-engine, sql-database
ms.reviewer: 
ms.service: sql-database
ms.component: system-stored-procedures
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_wait_for_database_copy_sync_TSQL
- sp_wait_for_database_copy_sync
dev_langs:
- TSQL
helpviewer_keywords:
- sp_wait_for_database_copy_sync
ms.assetid: 7068da7f-cb74-47f2-b064-eb076a0d3885
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6ca693b57fe2178a1b817ca76579ad3e7194f7c0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="active-geo-replication---spwaitfordatabasecopysync"></a>Replica geografica attiva - sp_wait_for_database_copy_sync
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Questa procedura è determinata da una relazione della [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] tra un database primario e uno secondario. La chiamata di **sp_wait_for_database_copy_sync** fa sì che l'applicazione in attesa fino a quando tutte le transazioni completate vengono replicate e del relativo riconoscimento dal database secondario attivo. Eseguire **sp_wait_for_database_copy_sync** solo sul database primario.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_wait_for_database_copy_sync [ @target_server = ] 'server_name'   
     , [ @target_database = ] 'database_name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @target_server =] 'nome_server'  
 Nome del server di database SQL che ospita il database secondario attivo. server_name è di tipo sysname e non prevede alcun valore predefinito.  
  
 [ @target_database = ] 'database_name'  
 Nome del database secondario attivo. database_name è di tipo sysname e non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Restituisce 0 per l'esito positivo o un numero di errore per l'esito negativo.  
  
 Le condizioni di errore più probabili sono:  
  
-   Il nome del server o il nome del database non è specificato.  
  
-   Il collegamento al nome del server o al database specificato non viene trovato.  
  
-   La connettività dell'interlink viene persa. **sp_wait_for_database_copy_sync** verrà restituito dopo il timeout della connessione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Qualsiasi utente nel database primario può chiamare questa stored procedure di sistema. L'account di accesso deve essere un utente in entrambi i database primario e secondario attivo.  
  
## <a name="remarks"></a>Osservazioni  
 Tutte le transazioni completate prima di un **sp_wait_for_database_copy_sync** chiamata vengono inviati al database secondario attivo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene richiamato **sp_wait_for_database_copy_sync** per garantire che tutte le transazioni vengano eseguito il commit nel database primario, db0 vengano inviate al database secondario attivo in ubfyu5ssyt di server di destinazione.  
  
```  
USE db0;  
GO  
EXEC sys.sp_wait_for_database_copy_sync @target_server = N'ubfyu5ssyt1', @target_database = N'db0';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys.dm continuous_copy_status &#40; Database SQL di Azure &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-continuous-copy-status-azure-sql-database.md)   
 [Funzioni e viste a gestione dinamica replica geografica &#40; Database SQL di Azure &#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)  
  
  
