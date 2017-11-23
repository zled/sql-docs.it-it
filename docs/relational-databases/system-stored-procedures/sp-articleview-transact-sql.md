---
title: sp_articleview (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_articleview
- sp_articleview_TSQL
helpviewer_keywords: sp_articleview
ms.assetid: a3d63fd6-f360-4a2f-8a82-a0dc15f650b3
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 165f494482aaac169eef7137bd0b45c0fa8b55d7
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sparticleview-transact-sql"></a>sp_articleview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea la vista che definisce l'articolo pubblicato quando una tabella viene filtrata in senso verticale o orizzontale. Questa vista viene utilizzata come origine filtrata dello schema e dei dati per le tabelle di destinazione. Solo gli articoli non sottoscritti possono essere modificati tramite questa stored procedure. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_articleview [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @view_name = ] 'view_name']  
    [ , [ @filter_clause = ] 'filter_clause']  
    [ , [ @change_active = ] change_active ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @refreshsynctranprocs = ] refreshsynctranprocs ]  
    [ , [ @internal = ] internal ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione in cui è contenuto l'articolo. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@article=**] **'***articolo***'**  
 Nome dell'articolo. *articolo* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@view_name=**] **'***view_name***'**  
 Nome della vista che definisce l'articolo pubblicato. *view_name* è **nvarchar (386)**, con un valore predefinito è NULL.  
  
 [  **@filter_clause=**] **'***filter_clause***'**  
 Clausola di restrizione (WHERE) che definisce un filtro orizzontale. Quando si specifica la clausola di restrizione, omettere la parola chiave WHERE. *filter_clause* è **ntext**, con un valore predefinito è NULL.  
  
 [  **@change_active =** ] *change_active*  
 Consente di modificare le colonne delle pubblicazioni a cui sono associate sottoscrizioni. *change_active* è un **int**, il valore predefinito è **0**. Se **0**, le colonne non vengono modificate. Se **1**, le viste possono essere create o ricreate in articoli attivi a cui sono associate sottoscrizioni.  
  
 [  **@force_invalidate_snapshot =** ] *force_invalidate_snapshot*  
 Segnala che l'azione eseguita da questa stored procedure potrebbe invalidare uno snapshot esistente. *force_invalidate_snapshot* è un **bit**, il valore predefinito è **0**.  
  
 **0** specifica che le modifiche apportate all'articolo non invalidano lo snapshot. Se la stored procedure rileva che la modifica richiede un nuovo snapshot, viene generato un errore e non viene apportata alcuna modifica.  
  
 **1** specifica che le modifiche apportate all'articolo possono invalidare lo snapshot potrebbe non essere valido e se sono disponibili sottoscrizioni che richiedono un nuovo snapshot, consente lo snapshot esistente deve essere contrassegnato come obsoleto e di generarne uno nuovo.  
  
 [  **@force_reinit_subscription =]** *force_reinit_subscription*  
 Segnala che l'azione eseguita dalla stored procedure potrebbe richiedere la reinizializzazione delle sottoscrizioni esistenti. *force_reinit_subscription* è un **bit** il valore predefinito è **0**.  
  
 **0** specifica che le modifiche apportate all'articolo non causano la reinizializzazione della sottoscrizione. Se la stored procedure rileva che la modifica richiede la reinizializzazione delle sottoscrizioni, viene generato un errore e non viene apportata alcuna modifica.  
  
 **1** specifica che le modifiche apportate all'articolo determina reinizializzazione della sottoscrizione esistente e concede l'autorizzazione per la reinizializzazione della sottoscrizione.  
  
 [  **@publisher** =] **'***publisher***'**  
 Specifica un non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione. *server di pubblicazione* è **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  *server di pubblicazione* non deve essere utilizzato per la pubblicazione da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione.  
  
 [  **@refreshsynctranprocs**  =] *refreshsynctranprocs*  
 Indica che le stored procedure utilizzate per sincronizzare la replica vengono ricreate automaticamente. *refreshsynctranprocs* è **bit**, con un valore predefinito è 1.  
  
 **1** indica che le stored procedure vengono ricreate.  
  
 **0** indica che le stored procedure non vengono ricreate.  
  
 [  **@internal** =] *interno*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_articleview** crea la vista che definisce l'articolo pubblicato e inserisce l'ID della vista nella **sync_objid** colonna il [sysarticles &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) table e inserisce il testo della clausola di restrizione nella **filter_clause** colonna. Se tutte le colonne vengono replicate e non esiste alcun **filter_clause**, **sync_objid** nel [sysarticles &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) tabella è impostata su, l'ID della tabella di base e l'utilizzo di **sp_articleview** non è obbligatorio.  
  
 Per pubblicare una tabella filtrata in verticale (ovvero, per filtrare le colonne) prima di eseguire **sp_addarticle** senza *sync_object* parametro, eseguire [sp_articlecolumn &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) una volta per ogni colonna da replicare (che definisce il filtro verticale) e quindi eseguire **sp_articleview** per creare la vista che definisce l'articolo pubblicato.  
  
 Per pubblicare una tabella filtrata in orizzontale (ovvero, per filtrare le righe), eseguire [sp_addarticle &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) senza *filtro* parametro. Eseguire [sp_articlefilter &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md), specificando tutti i parametri inclusi *filter_clause*. Eseguire quindi **sp_articleview**, specificando tutti i parametri con lo stesso *filter_clause*.  
  
 Per pubblicare una tabella filtrata in verticale e orizzontale, eseguire [sp_addarticle &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) senza *sync_object* o *filtro* parametri. Eseguire [sp_articlecolumn &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) una volta per ogni colonna da replicare e quindi eseguire [sp_articlefilter &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) e **sp_articleview**.  
  
 Se l'articolo include già una vista che definisce l'articolo pubblicato, **sp_articleview** Elimina la vista esistente e crea automaticamente uno nuovo. Se la vista è stata creata manualmente (**tipo** in [sysarticles &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md) è **5**), la vista esistente non è stata eliminata.  
  
 Se si crea una personalizzato stored procedure di filtro e una vista che definisce l'articolo pubblicato manualmente, non eseguire **sp_articleview**. Invece di fornire queste informazioni come il *filtro* e *sync_object* parametri [sp_addarticle &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md), insieme a appropriato *tipo* valore.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articleview-transact-_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_articleview**.  
  
## <a name="see-also"></a>Vedere anche  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [Definire e modificare un filtro di riga statico](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlefilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
