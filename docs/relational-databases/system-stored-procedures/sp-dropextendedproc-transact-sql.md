---
title: sp_dropextendedproc (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/04/2017
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
- sp_dropextendedproc
- sp_dropextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproc
ms.assetid: dd93af2c-1b7d-4e39-af23-2d21d270a381
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1c949cbe9e9c5e0f0c3bf7b823f47215cd5712b6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spdropextendedproc-transact-sql"></a>sp_dropextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina una stored procedure estesa.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Usare invece la funzionalità [Integrazione CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_dropextendedproc [ @functname = ] 'procedure'   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@functname =**] **'***procedura***'**  
 Nome della stored procedure estesa da eliminare. *procedura* è **nvarchar (517)**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 L'esecuzione di **sp_dropextendedproc** Elimina il nome la stored procedure estesa di definito dall'utente dal [Sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) vista del catalogo e rimuove la voce dal [extended_procedures ](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) vista del catalogo. Questa stored procedure può essere eseguita solo nel **master** database.  
  
**sp_dropextendedproc** non elimina le stored procedure estese di sistema. Al contrario, l'amministratore di sistema può negare l'autorizzazione EXECUTE per la stored procedure estesa per il **pubblica** ruolo.  
  
 **sp_dropextendedproc** non può essere eseguita all'interno di una transazione.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_dropextendedproc**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminata la stored procedure estesa `xp_hello`.  
  
> [!NOTE]  
>  Se questa stored procedure estesa non esiste, viene visualizzato un messaggio di errore.  
  
```  
USE master;  
GO  
EXEC sp_dropextendedproc 'xp_hello';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [la procedura sp_addextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
