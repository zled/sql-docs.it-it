---
title: sp_helpextendedproc (Transact-SQL) | Microsoft Docs
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
- sp_helpextendedproc
- sp_helpextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpextendedproc
ms.assetid: 7e1f017e-c898-4225-b375-6a73ef9aac7b
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: efc909fc4877d744cd99a5286426670aeffdefdf
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43033858"
---
# <a name="sphelpextendedproc-transact-sql"></a>sp_helpextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza le stored procedure estese definite e il nome della libreria a collegamento dinamico (DLL) a cui appartiene la procedura (funzione).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Usare invece la funzionalità [Integrazione CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpextendedproc [ [@funcname = ] 'procedure' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@funcname =**] **'***procedure***'**  
 Nome della stored procedure estesa su cui si desidera ottenere informazioni. *routine* viene **sysname**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome della stored procedure estesa.|  
|**DLL**|**nvarchar(255)**|Nome della DLL.|  
  
## <a name="remarks"></a>Note  
 Quando *routine* omette **sp_helpextendedproc** restituisce informazioni sulla stored procedure estesa. Quando questo parametro viene omesso, **sp_helpextendedproc** restituisce tutti i nomi di stored procedure e i nomi delle DLL a cui ogni stored procedure estesa estesi appartiene.  
  
## <a name="permissions"></a>Permissions  
 L'autorizzazione per eseguire **sp_helpextendedproc** viene concessa ai **pubblico**.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-reporting-help-on-all-extended-stored-procedures"></a>A. Restituzione di informazioni su tutte le stored procedure estese  
 Nell'esempio seguente vengono restituite informazioni su tutte le stored procedure estese.  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc;  
GO  
```  
  
### <a name="b-reporting-help-on-a-single-extended-stored-procedure"></a>B. Restituzione di informazioni su una sola stored procedure estesa  
 Nell'esempio seguente segnala il `xp_cmdshell` stored procedure estesa.  
  
```  
USE master;  
GO  
EXEC sp_helpextendedproc xp_cmdshell;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
