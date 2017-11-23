---
title: sp_addsynctriggers (Transact-SQL) | Documenti Microsoft
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
- sp_addsynctriggers_TSQL
- sp_addsynctriggers
helpviewer_keywords: sp_addsynctriggers
ms.assetid: e37d0c3b-19bf-4719-9535-96ba361372b3
caps.latest.revision: "29"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf7770a9388c18922aeb551246c314caba5860fe
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spaddsynctriggers-transact-sql"></a>sp_addsynctriggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea nel Sottoscrittore trigger utilizzati con tutti i tipi di sottoscrizioni aggiornabili, ovvero ad aggiornamento immediato, ad aggiornamento in coda e ad aggiornamento immediato sostituito dall'aggiornamento in coda in caso di errore. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
> [!IMPORTANT]  
>  Il [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) stored procedure deve essere utilizzata al posto di **sp_addsynctrigger**. [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md) genera uno script che contiene il **sp_addsynctrigger** chiamate.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addsynctriggers [ @sub_table = ] 'sub_table'  
        , [ @sub_table_owner = ] 'sub_table_owner'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @ins_proc = ] 'ins_proc'   
        , [ @upd_proc = ] 'upd_proc'   
        , [ @del_proc = ] 'del_proc'   
        , [ @cftproc = ] 'cftproc'  
        , [ @proc_owner = ] 'proc_owner'  
    [ , [ @identity_col = ] 'identity_col' ]  
    [ , [ @ts_col = ] 'timestamp_col' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]   
        , [ @primary_key_bitmap = ] 'primary_key_bitmap'  
    [ , [ @identity_support = ] identity_support ]  
    [ , [ @independent_agent = ] independent_agent ]  
        , [ @distributor = ] 'distributor'   
    [ , [ @pubversion = ] pubversion  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@sub_table=**] **'***sub_table***'**  
 Nome della tabella del Sottoscrittore. *sub_table* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@sub_table_owner=**] **'***sub_table_owner***'**  
 Nome del proprietario della tabella del Sottoscrittore. *sub_table_owner* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 Nome del database del server di pubblicazione. *publisher_db* è **sysname**, non prevede alcun valore predefinito. Se è NULL, viene utilizzato il database corrente.  
  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *Pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@ins_proc=**] **'***ins_proc***'**  
 Nome della stored procedure che supporta gli inserimenti tramite la sincronizzazione delle transazioni nel server di pubblicazione. *ins_proc* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@upd_proc=**] **'***upd_proc***'**  
 Nome della stored procedure che supporta gli aggiornamenti tramite la sincronizzazione delle transazioni nel server di pubblicazione. *ins_proc* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@del_proc=**] **'***del_proc***'**  
 Nome della stored procedure che supporta le eliminazioni tramite la sincronizzazione delle transazioni nel server di pubblicazione. *ins_proc* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@cftproc =** ] **'***cftproc***'**  
 Nome della procedura a generazione automatica utilizzata dalle pubblicazioni che consentono l'aggiornamento in coda. *cftproc* è **sysname**, non prevede alcun valore predefinito. Nel caso di pubblicazioni che consentono l'aggiornamento immediato, questo valore è NULL. Questo parametro viene applicato alle pubblicazioni che consentono l'aggiornamento in coda (aggiornamento in coda e aggiornamento immediato sostituito dall'aggiornamento in coda in caso di errore).  
  
 [  **@proc_owner =** ] **'***proc_owner***'**  
 Specifica l'account utente utilizzato nel server di pubblicazione per la creazione di tutte le stored procedure a generazione automatica per l'aggiornamento della pubblicazione (aggiornamento in coda e/o immediato). *proc_owner* è **sysname** prevede alcun valore predefinito.  
  
 [  **@identity_col=**] **'***identity_col***'**  
 Nome della colonna Identity nel server di pubblicazione. *identity_col* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@ts_col=**] **'***timestamp_col***'**  
 È il nome del **timestamp** colonna nel server di pubblicazione. *timestamp_col* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@filter_clause=**] **'***filter_clause***'**  
 Clausola di restrizione (WHERE) che definisce un filtro orizzontale. Quando si specifica la clausola di restrizione, omettere la parola chiave WHERE. *filter_clause*è **nvarchar (4000)**, con un valore predefinito è NULL.  
  
 [  **@primary_key_bitmap =**] **'***primary_key_bitmap***'**  
 Mappa di bit delle colonne chiave primaria nella tabella. *primary_key_bitmap* è **varbinary (4000)**, non prevede alcun valore predefinito.  
  
 [  **@identity_support =** ] *identity_support*  
 Abilita e disabilita la gestione automatica degli intervalli di valori Identity quando viene utilizzato l'aggiornamento in coda. *identity_support* è un **bit**, il valore predefinito è **0**. **0** significa che non vi è alcuna identità di intervalli di valori supportati, **1** consente la gestione di intervallo di valori identity automatico.  
  
 [  **@independent_agent =** ] *independent_agent*  
 Specifica se è disponibile un solo agente di distribuzione (agente indipendente) per la pubblicazione oppure un agente di distribuzione per ogni coppia database di pubblicazione/database di sottoscrizione (agente condiviso). Questo valore è determinato dal valore della proprietà independent_agent della pubblicazione definito nel server di pubblicazione. *independent_agent* è di tipo bit il valore predefinito è **0**. Se **0**, l'agente è un agente condiviso. Se **1**, l'agente è un agente indipendente.  
  
 [  **@distributor =** ] **'***distributore***'**  
 Nome del server di distribuzione. *server di distribuzione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@pubversion** =] *pubversion*  
 Indica la versione del server di pubblicazione. *pubversion* è **int**, con un valore predefinito è 1. **1** indica che la versione del server di pubblicazione è [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 2 o precedente. **2** indica che il server di pubblicazione [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Service Pack 3 (SP3) o versione successiva. *pubversion* deve essere impostata in modo esplicito su **2** quando la versione del server di pubblicazione è [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] SP3 o versione successiva.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addsynctriggers** viene utilizzata dall'agente di distribuzione come parte dell'inizializzazione della sottoscrizione. In genere, non viene eseguita dagli utenti, ma può risultare utile se l'utente deve configurare una sottoscrizione nosync in modo manuale.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addsynctriggers**.  
  
## <a name="see-also"></a>Vedere anche  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
