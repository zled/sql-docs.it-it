---
title: sp_articlefilter (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_articlefilter_TSQL
- sp_articlefilter
helpviewer_keywords:
- sp_articlefilter
ms.assetid: 4c3fee32-a43f-4757-a029-30aef4696afb
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1ec7582f644a3701ef209c2ad3d4774e1aefdfb5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sparticlefilter-transact-sql"></a>sp_articlefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Filtra i dati da pubblicare in base a un articolo di tabella. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_articlefilter [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @filter_name = ] 'filter_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione in cui è contenuto l'articolo. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@article=**] **'***articolo***'**  
 Nome dell'articolo. *articolo* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@filter_name=**] **'***filter_name***'**  
 Nome della stored procedure di filtro da creare dal *filter_name*. *filter_name* viene **nvarchar(386)**, con un valore predefinito è NULL. È necessario specificare un nome univoco per il filtro per gli articoli.  
  
 [  **@filter_clause=**] **'***filter_clause***'**  
 Clausola di restrizione (WHERE) che definisce un filtro orizzontale. Quando si specifica la clausola di restrizione, omettere la parola chiave WHERE. *filter_clause* viene **ntext**, con un valore predefinito è NULL.  
  
 [ **@force_invalidate_snapshot =** ] *force_invalidate_snapshot*  
 Segnala che l'azione eseguita da questa stored procedure potrebbe invalidare uno snapshot esistente. *force_invalidate_snapshot* è un **bit**, il valore predefinito è **0**.  
  
 **0** specifica che le modifiche apportate all'articolo non invalidano lo snapshot non è valido. Se la stored procedure rileva che la modifica richiede un nuovo snapshot, viene generato un errore e non viene apportata alcuna modifica.  
  
 **1** specifica che le modifiche apportate all'articolo possono invalidare lo snapshot non è valido e se sono disponibili sottoscrizioni che richiedono un nuovo snapshot, consente l'autorizzazione per lo snapshot esistente deve essere contrassegnato come obsoleto e di generarne uno nuovo.  
  
 [  **@force_reinit_subscription =** ] *force_reinit_subscription*  
 Segnala che l'azione eseguita dalla stored procedure potrebbe richiedere la reinizializzazione delle sottoscrizioni esistenti. *force_reinit_subscription* è un **bit**, il valore predefinito è **0**.  
  
 **0** specifica che le modifiche apportate all'articolo non causano la necessità di reinizializzazione delle sottoscrizioni. Se la stored procedure rileva che la modifica richiede la reinizializzazione delle sottoscrizioni, viene generato un errore e non viene apportata alcuna modifica.  
  
 **1** specifica che le modifiche apportate all'articolo causa reinizializzazione delle sottoscrizioni esistenti e concede l'autorizzazione per la reinizializzazione.  
  
 [  **@publisher=** ] **'***publisher***'**  
 Specifica un non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  *server di pubblicazione* non deve essere utilizzato con un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_articlefilter** viene utilizzata nella replica snapshot e transazionale.  
  
 L'esecuzione di **sp_articlefilter** per un articolo con le sottoscrizioni esistenti, è necessario che tali reinizializzazione delle sottoscrizioni.  
  
 **sp_articlefilter** crea il filtro, inserisce l'ID della stored procedure di filtro nel **filtro** colonna del [sysarticles &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) tabella, quindi Inserisce il testo della clausola di restrizione nella **filter_clause** colonna.  
  
 Per creare un articolo con un filtro orizzontale, eseguire [sp_addarticle &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) senza alcun *filtro* parametro. Eseguire **sp_articlefilter**, specificando tutti i parametri inclusi *filter_clause*, quindi eseguire [sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md), specificando tutti i parametri con lo stesso *filter_clause*. Se il filtro è già presente e se il **tipo** in **sysarticles** è **1** (articolo basato su log), il filtro precedente viene eliminato e viene creato un nuovo filtro.  
  
 Se *filter_name* e *filter_clause* vengono omessi, il filtro precedente viene eliminato e l'ID del filtro è impostato su **0**.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlefilter-transac_1.sql)]  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_articlefilter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Definire e modificare un filtro di riga statico](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articleview &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
