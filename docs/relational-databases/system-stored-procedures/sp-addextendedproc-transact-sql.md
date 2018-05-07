---
title: la procedura sp_addextendedproc (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addextendedproc_TSQL
- sp_addextendedproc
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addextendedproc
ms.assetid: c0d4b47b-a855-451e-90e5-5fb2d836ebfa
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2083d370479fa19049a083ef401574f21740929c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="spaddextendedproc-transact-sql"></a>sp_addextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Registra il nome di una nuova stored procedure estesa in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Usare invece la funzionalità [Integrazione CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addextendedproc [ @functname = ] 'procedure' ,   
     [ @dllname = ] 'dll'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@functname =** ] **'***procedure***'**  
 Nome della funzione da chiamare all'interno della libreria di collegamento dinamico (DDL, Dynamic-Link Library). *stored procedure* viene **nvarchar(517)**, non prevede alcun valore predefinito. *stored procedure* può includere facoltativamente il nome del proprietario nel formato *proprietario*.  
  
 [  **@dllname =** ] **'***dll***'**  
 Nome della DLL che contiene la funzione. *DLL* viene **nvarchar (255)**, non prevede alcun valore predefinito. È consigliabile specificare il percorso completo della DLL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Dopo la creazione di una stored procedure estesa, è necessario aggiungerlo a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando **sp_addextendedproc**. Per ulteriori informazioni, vedere [aggiunta di una Stored Procedure estesa a SQL Server](../../relational-databases/extended-stored-procedures-programming/adding-an-extended-stored-procedure-to-sql-server.md).  
  
 Questa procedura può essere eseguita solo nel **master** database. Per eseguire una stored procedure estesa da un database diverso da **master**, qualificare il nome della stored procedure estesa con **master**.  
  
 **la procedura sp_addextendedproc** aggiunge voci per il [Sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) vista del catalogo, la registrazione del nome della nuova stored procedure estesa in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Aggiunge inoltre una voce di [extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) vista del catalogo.  
  
> [!IMPORTANT]  
>  Le DLL esistenti non registrate con un percorso completo non funzionano dopo l'aggiornamento a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per risolvere il problema, utilizzare **sp_dropextendedproc** per annullare la registrazione della DLL e quindi registrarla **sp_addextendedproc**, specificando il percorso completo.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_addextendedproc**.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente aggiunge il **xp_hello** stored procedure estesa.  
  
```  
USE master;  
GO  
EXEC sp_addextendedproc xp_hello, 'c:\xp_hello.dll';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
