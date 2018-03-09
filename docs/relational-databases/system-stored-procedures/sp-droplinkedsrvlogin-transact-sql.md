---
title: la procedura sp_droplinkedsrvlogin (Transact-SQL) | Documenti Microsoft
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
- sp_droplinkedsrvlogin_TSQL
- sp_droplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droplinkedsrvlogin
ms.assetid: 75a4a040-72d5-4d29-8304-de0aa481ad4b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a0d9e2ed37bd70dda7d1cf47f78a7f1c28692a0f
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spdroplinkedsrvlogin-transact-sql"></a>sp_droplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un mapping esistente tra un account di accesso nel server locale in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione e un account di accesso nel server collegato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_droplinkedsrvlogin [ @rmtsrvname= ] 'rmtsrvname' ,   
   [ @locallogin= ] 'locallogin'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@rmtsrvname =** ] **'***rmtsrvname***'**  
 È il nome di un server collegato che il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene applicato il mapping di account di accesso. *rmtsrvname* è **sysname**, non prevede alcun valore predefinito. *rmtsrvname* deve essere già esistente.  
  
 [  **@locallogin =** ] **'***locallogin***'**  
 È il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso nel server locale che dispone di un mapping per il server collegato *rmtsrvname*. *locallogin* è **sysname**, non prevede alcun valore predefinito. Un mapping per *locallogin* a *rmtsrvname* deve essere già esistente. Se NULL, il mapping predefinito creato tramite **sp_addlinkedserver**, che esegue il mapping di tutti gli account di accesso nel server locale per gli account di accesso nel server collegato, viene eliminato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Quando il mapping esistente per un account di accesso viene eliminato, il server locale viene utilizzato il mapping predefinito creato da **sp_addlinkedserver** quando si connette al server collegato per conto di tale account di accesso. Per modificare il mapping predefinito, utilizzare **sp_addlinkedsrvlogin**.  
  
 Se viene eliminato anche il mapping predefinito, solo gli account di accesso in modo esplicito assegnato un mapping di account di accesso al server collegato, utilizzando **sp_addlinkedsrvlogin**, possono accedere al server collegato.  
  
 **la procedura sp_droplinkedsrvlogin** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY LOGIN nel server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-removing-the-login-mapping-for-an-existing-user"></a>A. Rimozione del mapping di accesso per un utente esistente  
 Nell'esempio seguente viene rimosso il mapping per l'account di accesso `Mary` tra il server locale e il server collegato `Accounts`. L'account di accesso `Mary` utilizzerà pertanto il mapping predefinito degli account di accesso.  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', 'Mary';  
```  
  
### <a name="b-removing-the-default-login-mapping"></a>B. Rimozione del mapping predefinito degli account di accesso  
 Nell'esempio seguente viene rimosso il mapping predefinito degli account di accesso creato tramite `sp_addlinkedserver` nel server locale `Accounts`.  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', NULL;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [la procedura sp_addlinkedsrvlogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
