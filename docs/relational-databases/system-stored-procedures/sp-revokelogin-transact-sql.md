---
title: sp_revokelogin (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 0d59e993563b340b7016887720fb8f3638dca247
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sprevokelogin-transact-sql"></a>sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove le voci di account di accesso da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per un utente di Windows o un gruppo creato mediante CREATE LOGIN, **sp_grantlogin**, o **sp_denylogin**.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Uso [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@loginame=**] **'***account di accesso***'**  
 Nome dell'utente o del gruppo di Windows. *account di accesso* viene **sysname**, non prevede alcun valore predefinito. *account di accesso* può essere qualsiasi nome utente di Windows esistente o un gruppo nel formato *nome del Computer*\\*utente o dominio*\\*utente*.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_revokelogin** disabilita le connessioni che utilizzano l'account specificato per il *accesso* parametro. Gli utenti di Windows ai quali è stato concesso l'accesso a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite l'appartenenza a un gruppo di Windows possono tuttavia continuare a connettersi come gruppo dopo la revoca del proprio accesso individuale. Analogamente, se il *accesso* parametro specifica il nome di un gruppo di Windows, i membri del gruppo che sono stati separatamente concesso l'accesso all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sarà comunque in grado di connettersi.  
  
 Ad esempio, se utente di Windows **ADVWORKS\john** è un membro del gruppo di Windows **ADVWORKS\Admins**, e **sp_revokelogin** revochi l'accesso di `ADVWORKS\john`:  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 Utente **ADVWORKS\john** può comunque connettersi se **ADVWORKS\Admins** è stato concesso l'accesso a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Analogamente, se il gruppo di Windows **ADVWORKS\Admins** l'accesso revocato ma **ADVWORKS\john** è concesso l'accesso, **ADVWORKS\john** possono comunque connettersi.  
  
 Utilizzare **sp_denylogin** in modo esplicito impedire agli utenti di connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], indipendentemente dall'appartenenza al gruppo di Windows.  
  
 **sp_revokelogin** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER ANY LOGIN nel server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono rimosse le voci dell'account di accesso per l'utente di Windows `Corporate\MollyA`.  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 Oppure  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN & #40; Transact-SQL & #41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
