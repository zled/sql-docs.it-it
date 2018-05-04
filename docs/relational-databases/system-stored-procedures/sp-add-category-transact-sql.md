---
title: sp_add_category (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_category
- sp_add_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_category
ms.assetid: 6cca32cd-d941-4378-aed6-a7c90cb7520a
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc390561febba64b77010ba80feaa151f05f534b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spaddcategory-transact-sql"></a>sp_add_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge al server la categoria specificata di processi, avvisi o operatori.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_category   
     [ [ @class = ] 'class', ]   
     [ [ @type = ] 'type', ]   
     { [ @name = ] 'name' }  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@class =** ] **'***classe***'**  
 Classe della categoria da aggiungere. *classe* viene **varchar (8)** con un valore predefinito di processo, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|JOB|Aggiunge una categoria di processi.|  
|ALERT|Aggiunge una categoria di avvisi.|  
|OPERATOR|Aggiunge una categoria di operatori.|  
  
 [  **@type =** ] **'***tipo***'**  
 Tipo della categoria da aggiungere. *tipo di* viene **varchar(12)**, con valore predefinito è **locale**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|LOCAL|Categoria di processi locali.|  
|MULTI-SERVER|Categoria di processi multiserver.|  
|Nessuno|Una categoria per una classe diversa da JOB **.**|  
  
 [  **@name =** ] **'***nome***'**  
 Nome della categoria da aggiungere. Il nome deve essere univoco all'interno della classe specificata. *nome* viene **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_add_category** deve essere eseguita la **msdb** database.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_add_category**.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene creata la categoria di processi locale `AdminJobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_category  
    @class=N'JOB',  
    @type=N'LOCAL',  
    @name=N'AdminJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_delete_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_help_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [sp_update_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [dbo.sysjobs & #40; Transact-SQL & #41;](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md)   
 [dbo.sysjobservers &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
