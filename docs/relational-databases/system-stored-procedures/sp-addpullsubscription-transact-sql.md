---
title: sp_addpullsubscription (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
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
- sp_addpullsubscription
- sp_addpullsubscription_TSQL
helpviewer_keywords: sp_addpullsubscription
ms.assetid: 0f4bbedc-0c1c-414a-b82a-6fd47f0a6a7f
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b6c772cc91d922ceb8acd5c205c9b19dc67d50d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spaddpullsubscription-transact-sql"></a>sp_addpullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge una sottoscrizione pull a una pubblicazione snapshot o transazionale. Questa stored procedure viene eseguita nel Sottoscrittore nel database in cui deve essere creata la sottoscrizione pull.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addpullsubscription [ @publisher= ] 'publisher'  
    [ , [ @publisher_db= ] 'publisher_db' ]  
        , [ @publication= ] 'publication'  
    [ , [ @independent_agent= ] 'independent_agent' ]  
    [ , [ @subscription_type= ] 'subscription_type' ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @update_mode= ] 'update_mode' ]  
    [ , [ @immediate_sync = ] immediate_sync ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 Nome del database del server di pubblicazione. *publisher_db* è **sysname**, con un valore predefinito è NULL. *publisher_db* viene ignorata dal server di pubblicazione Oracle.  
  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@independent_agent=**] **'***independent_agent***'**  
 Specifica se per la pubblicazione è disponibile un agente di distribuzione autonomo. *independent_agent* è **nvarchar (5)**, con un valore predefinito è TRUE. Se **true**, è disponibile un agente di distribuzione autonomo per la pubblicazione. Se **false**, è associato un agente di distribuzione per ogni coppia database del server di pubblicazione/sottoscrizione di database. *independent_agent* è una proprietà della pubblicazione e deve avere lo stesso valore qui perché contiene server di pubblicazione.  
  
 [  **@subscription_type=**] **'***subscription_type***'**  
 Tipo di sottoscrizione. *subscription_type* è **nvarchar(9)**, il valore predefinito è **anonimo**. È necessario specificare un valore di **pull** per *subscription_type*, a meno che non si desidera creare una sottoscrizione senza la registrazione della sottoscrizione nel server di pubblicazione. In questo caso, è necessario specificare un valore di **anonimo**. Questa operazione è necessaria per i casi in cui è possibile stabilire un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connessione al server di pubblicazione durante la configurazione della sottoscrizione.  
  
 [  **@description=**] **'***descrizione***'**  
 Descrizione della pubblicazione. *Descrizione* è **nvarchar (100)**, con un valore predefinito è NULL.  
  
 [  **@update_mode=**] **'***update_mode***'**  
 Tipo di aggiornamento. *update_mode* è **nvarchar (30)**, e può essere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**sola lettura** (impostazione predefinita)|La sottoscrizione è di sola lettura. Le modifiche apportate nel Sottoscrittore non vengono ritrasmesse al server di pubblicazione. È consigliabile utilizzare questo valore quando non sono previsti aggiornamenti nel Sottoscrittore.|  
|**Synctran**|Abilita il supporto per sottoscrizioni ad aggiornamento immediato.|  
|**in coda tran**|Abilita la sottoscrizione per l'aggiornamento in coda. Le modifiche dei dati possono essere apportate nel Sottoscrittore, archiviate in una coda e quindi distribuite al server di pubblicazione.|  
|**failover**|Abilita la sottoscrizione per l'aggiornamento immediato sostituito dall'aggiornamento in coda in caso di failover. Le modifiche dei dati possono essere apportate nel Sottoscrittore e distribuite immediatamente al server di pubblicazione. Se il server di pubblicazione e il Sottoscrittore non sono connessi, le modifiche apportate ai dati nel Sottoscrittore possono essere archiviate in una coda fino al ripristino della connessione tra il Sottoscrittore e il server di pubblicazione.|  
|**failover in coda**|Abilita la sottoscrizione come sottoscrizione con aggiornamento in coda con la possibilità di passare alla modalità di aggiornamento immediato. Le modifiche ai dati possono essere apportate nel Sottoscrittore e archiviate in una coda fino alla riconnessione del Sottoscrittore e del server di pubblicazione. Quando viene ristabilita una connessione continua, la modalità di aggiornamento può essere modificata nella modalità di aggiornamento immediato. *Non supportato per il server di pubblicazione Oracle*.|  
  
 [  **@immediate_sync =**] *immediate_sync*  
 Indica se i file di sincronizzazione vengono creati o ricreati a ogni esecuzione dell'agente snapshot. *immediate_sync* è **bit** con un valore predefinito è 1 e deve essere impostato sullo stesso valore di *immediate_sync* in **sp_addpublication**. *immediate_sync* è una proprietà della pubblicazione e deve avere lo stesso valore qui perché contiene server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_addpullsubscription** viene utilizzata nella replica snapshot e transazionale.  
  
> [!IMPORTANT]  
>  Per le sottoscrizioni ad aggiornamento in coda utilizzare l'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per le connessioni ai Sottoscrittori e specificare un account diverso per la connessione a ogni Sottoscrittore. Quando si crea una sottoscrizione pull che supporta l'aggiornamento in coda, la replica imposta sempre la connessione per l'utilizzo dell'autenticazione di Windows. Per le sottoscrizioni pull, il sistema di replica non è in grado di accedere ai metadati nel Sottoscrittore necessari per l'utilizzo dell'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In questo caso, è necessario eseguire [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md) per modificare la connessione da utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticazione dopo aver configurata la sottoscrizione.  
  
 Se il [MSreplication_subscriptions &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) tabella non esiste nel Sottoscrittore, **sp_addpullsubscription** lo crea. Aggiunge inoltre una riga per il [MSreplication_subscriptions &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md) tabella. Per le sottoscrizioni pull, [sp_addsubscription &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) deve essere chiamato prima del server di pubblicazione.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_addtranpullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addpullsubscription-t_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_addpullsubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Creare una sottoscrizione aggiornabile di una pubblicazione transazionale](../../relational-databases/replication/publish/create-updatable-subscription-to-transactional-publication.md) [sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpullsubscription_agent &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md)   
 [sp_change_subscription_properties &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_droppullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [sp_helppullsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
