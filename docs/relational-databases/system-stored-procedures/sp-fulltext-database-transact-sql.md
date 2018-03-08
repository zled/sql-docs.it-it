---
title: sp_fulltext_database (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ec46eab309234379000bfcc6ea0a0245450e868
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spfulltextdatabase-transact-sql"></a>sp_fulltext_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Non ha alcun effetto sui cataloghi full-text in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive ed è supportata solo per la compatibilità con le versioni precedenti. **sp_fulltext_database** non disabilita il motore Full-Text per un determinato database. Tutti i database creati dall'utente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sono sempre abilitati per l'indicizzazione full-text.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] In alternativa, usare [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@action=**] **'***azione***'**  
 Azione da eseguire. **azione** è **varchar (20)**, i possibili valori sono i seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**enable**|Supportata unicamente per compatibilità con le versioni precedenti. Non produce alcun effetto sui cataloghi full-text in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive.|  
|**disable**|Supportata unicamente per compatibilità con le versioni precedenti. Non produce alcun effetto sui cataloghi full-text in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] e versioni successive, non è possibile disabilitare l'indicizzazione full-text. Disabilitare l'indicizzazione full-text non rimuove le righe da **sysfulltextcatalogs** e indicare che le tabelle abilitate full-text non sono più contrassegnate per l'indicizzazione full-text. Tutte le definizioni di metadati full-text vengono conservate nelle tabelle di sistema.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server e **db_owner** ruolo predefinito del database possono eseguire **sp_fulltext_database**.  
  
## <a name="see-also"></a>Vedere anche  
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
