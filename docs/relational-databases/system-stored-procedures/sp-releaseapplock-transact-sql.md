---
title: sp_releaseapplock (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_releaseapplock_TSQL
- sp_releaseapplock
dev_langs: TSQL
helpviewer_keywords: sp_releaseapplock
ms.assetid: 51b03c2f-0d54-40f5-9172-e747942d4a46
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5eb17b39125209ca15214356e84f832e2f8cbc73
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spreleaseapplock-transact-sql"></a>sp_releaseapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Rilascia un blocco in una risorsa di applicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_releaseapplock [ @Resource = ] 'resource_name'   
     [ , [ @LockOwner = ] 'lock_owner' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @Resource=] '*resource_name*'  
 Nome di una risorsa di blocco specificato nell'applicazione client. L'applicazione deve garantire che la risorsa sia univoca. Il nome specificato viene sottoposto internamente ad hashing per creare un valore che è possibile archiviare in Gestione blocchi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name* è **nvarchar (255)** prevede alcun valore predefinito. *resource_name* è binario rispetto, pertanto è tra maiuscole e minuscole indipendentemente dalle impostazioni delle regole di confronto del database corrente.  
  
 [ @LockOwner=] '*lock_owner*'  
 È il proprietario del blocco, ovvero il *lock_owner* valore quando è stato richiesto il blocco. *lock_owner* è **nvarchar(32)**. Il valore può essere **transazione** (impostazione predefinita) o **sessione**. Quando il *lock_owner* valore **transazione**, predefinito o specificato in modo esplicito, sp_getapplock deve essere eseguito all'interno di una transazione.  
  
 [ @DbPrincipal=] '*database_principal*'  
 Utente, ruolo o ruolo applicazione al quale sono state assegnate autorizzazioni per un oggetto di un database. Il chiamante della funzione deve essere un membro di *database_principal*, dbo o db_owner ruolo predefinito del database per chiamare la funzione correttamente. Il valore predefinito è public.  
  
## <a name="return-code-values"></a>Valori restituiti  
 \>= 0 (esito positivo), or < 0 (esito negativo)  
  
|Valore|Risultato|  
|-----------|------------|  
|0|Il blocco è stato rilasciato correttamente.|  
|-999|Indica un errore di convalida dei parametri o un altro errore di chiamata.|  
  
## <a name="remarks"></a>Osservazioni  
 Se un'applicazione richiama sp_getapplock più volte per la stessa risorsa di blocco, per rilasciare il blocco è necessario richiamare sp_releaseapplock lo stesso numero di volte.  
  
 I blocchi vengono inoltre rilasciati quando per qualsiasi motivo il server viene arrestato.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rilasciato il blocco associato alla transazione corrente nella risorsa `Form1` del database `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'Form1',   
     @LockMode = 'Shared';  
EXEC sp_releaseapplock @DbPrincipal = 'dbo', @Resource = 'Form1';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [APPLOCK_MODE &#40; Transact-SQL &#41;](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40; Transact-SQL &#41;](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_getapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
  
  
