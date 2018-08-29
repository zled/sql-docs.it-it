---
title: sp_droptype (Transact-SQL) | Microsoft Docs
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
- sp_droptype_TSQL
- sp_droptype
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droptype
ms.assetid: e78464ac-2370-4c4e-9cc0-06aebc07cec5
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0acf840ba2e117fd27539fe356431881f1fc91c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020215"
---
# <a name="spdroptype-transact-sql"></a>sp_droptype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Elimina un tipo di dati alias da **systypes**.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_droptype [ @typename = ] 'type'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@typename=**] **'***tipo***'**  
 Nome di un tipo di dati alias di cui si è proprietari. *tipo di* viene **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-type"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="remarks"></a>Note  
 Il **tipo** alias tipo di dati non può essere eliminato se vi fanno riferimento le tabelle o altri oggetti di database.  
  
> [!NOTE]  
>  Non è possibile eliminare un tipo di dati alias utilizzato all'interno di una definizione di tabella oppure a cui è associata una regola o un valore predefinito.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'appartenenza al **db_owner** ruolo predefinito del database o il **db_ddladmin** ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminato il tipo di dati alias `birthday`.  
  
> [!NOTE]  
>  Se questo tipo di dati alias non esiste, viene visualizzato un messaggio di errore.  
  
```  
USE master;  
GO  
EXEC sp_droptype 'birthday';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database le Stored procedure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_addtype &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addtype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
