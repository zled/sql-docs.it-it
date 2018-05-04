---
title: sp_dropmergefilter (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_dropmergefilter_TSQL
- sp_dropmergefilter
helpviewer_keywords:
- sp_dropmergefilter
ms.assetid: 798586d7-05f3-4a5e-bea8-a34b7b52d0fd
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d4575ae38c0ff0397c01a4f4966503e1129b94e7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spdropmergefilter-transact-sql"></a>sp_dropmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina un filtro di merge. **sp_dropmergefilter** Elimina tutte le colonne di filtro merge definite nel filtro che si desidera eliminare. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dropmergefilter [ @publication= ] 'publication', [ @article= ] 'article'     , [ @filtername= ] 'filtername'  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@article=**] **'***articolo***'**  
 Nome dell'articolo. *articolo* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@filtername=**] **'***filtername***'**  
 Nome del filtro che si desidera eliminare. *FilterName* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@force_invalidate_snapshot=** ] *force_invalidate_snapshot*  
 Abilita o disabilita la funzionalità che consente di invalidare uno snapshot. *force_invalidate_snapshot* è un **bit**, con un valore predefinito **0**.  
  
 **0** specifica che le modifiche apportate all'articolo di merge non invalidano lo snapshot non è valido.  
  
 **1** specifica che le modifiche apportate all'articolo di merge potrebbero invalidare lo snapshot non è valido. Se è questo il caso, il valore **1** concede l'autorizzazione per l'esecuzione del nuovo snapshot.  
  
 [ **@force_reinit_subscription**=] *force_reinit_subscription*  
 Abilita o disabilita la possibilità di contrassegnare una sottoscrizione come non valida. *force_reinit_subscription* è un **bit**, con un valore predefinito **0**.  
  
 **0** specifica che le modifiche apportate al filtro di articolo di merge non invalidano le sottoscrizioni non è valido.  
  
 **1** indica che le modifiche apportate al filtro di articolo di merge causano le sottoscrizioni non è valido.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_dropmergefilter** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_dropmergefilter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica delle proprietà di pubblicazioni e articoli](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_helpmergefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
