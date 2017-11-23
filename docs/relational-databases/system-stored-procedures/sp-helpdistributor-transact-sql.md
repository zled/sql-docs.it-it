---
title: sp_helpdistributor (Transact-SQL) | Documenti Microsoft
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
- sp_helpdistributor_TSQL
- sp_helpdistributor
helpviewer_keywords: sp_helpdistributor
ms.assetid: 37b0983e-3b69-4f0f-977e-20efce0a0b97
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f8436c56ec260fdf2f22d5f6ecdb7a1c3102d6be
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpdistributor-transact-sql"></a>sp_helpdistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elenca le informazioni sul server di distribuzione, database di distribuzione, directory di lavoro e [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account utente dell'agente. Questa stored procedure viene eseguita nel database di pubblicazione o in qualsiasi database del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdistributor [ [ @distributor= ] 'distributor' OUTPUT ]  
    [ , [ @distribdb= ] 'distribdb' OUTPUT ]  
    [ , [ @directory= ] 'directory' OUTPUT ]  
    [ , [ @account= ] 'account' OUTPUT ]  
    [ , [ @min_distretention= ] min_distretention OUTPUT ]  
    [ , [ @max_distretention= ] max_distretention OUTPUT ]  
    [ , [ @history_retention= ] history_retention OUTPUT ]  
    [ , [ @history_cleanupagent= ] 'history_cleanupagent' OUTPUT ]  
    [ , [ @distrib_cleanupagent = ] 'distrib_cleanupagent' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @local = ] 'local' ]  
    [ , [ @rpcsrvname= ] 'rpcsrvname' OUTPUT ]  
    [ , [ @publisher_type = ] 'publisher_type' OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@distributor=**] **'***distributore***'** OUTPUT  
 Nome del server di distribuzione. Server di distribuzione è **sysname**, il valore predefinito è  **%** , che è l'unico valore che restituisce un set di risultati.  
  
 [  **@distribdb=**] **'***distribdb***'** OUTPUT  
 Nome del database di distribuzione. *distribdb* è **sysname**, il valore predefinito è  **%** , che è l'unico valore che restituisce un set di risultati.  
  
 [  **@directory=**] **'***directory***'** OUTPUT  
 Directory di lavoro. *directory* è **nvarchar (255)**, il valore predefinito è  **%** , che è l'unico valore che restituisce un set di risultati.  
  
 [  **@account=**] **'***account***' OUTPUT**  
 Account utente di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. *account*è **nvarchar (255)**, il valore predefinito è  **%** , che è l'unico valore che restituisce un set di risultati.  
  
 [  **@min_distretention=**] *min_distretention***OUTPUT**  
 Periodo di memorizzazione minimo per la distribuzione espresso in ore. *min_distretention* è **int**, il valore predefinito è **-1**.  
  
 [  **@max_distretention=**] *max_distretention***OUTPUT**  
 Periodo di memorizzazione massimo per la distribuzione espresso in ore. *max_distretention* è **int**, il valore predefinito è **-1**.  
  
 [  **@history_retention=**] *history_retention***OUTPUT**  
 Periodo di memorizzazione della cronologia espresso in ore. *history_retention* è **int**, il valore predefinito è **-1**.  
  
 [  **@history_cleanupagent=**] **'***history_cleanupagent***' OUTPUT**  
 Nome dell'agente per la pulizia del contenuto della cronologia. *history_cleanupagent* è **nvarchar (100)**, il valore predefinito è  **%** , che è l'unico valore che restituisce un set di risultati.  
  
 [  **@distrib_cleanupagent =**] **'***distrib_cleanupagent***' OUTPUT**  
 Nome dell'agente per l'eliminazione dei riferimenti di distribuzione *distrib_cleanupagent* è **nvarchar (100)**, il valore predefinito è  **%** , che è l'unico valore che restituisce un set di risultati.  
  
 [  **@publisher=**] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@local=**] **'***locale***'**  
 Indica se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve recuperare o meno i valori del server locale. *locale* è **nvarchar (5)**, con un valore predefinito è NULL.  
  
 [  **@rpcsrvname=**] **'***rpcsrvname***' OUTPUT**  
 Nome del server che esegue chiamate di procedure remote. *rpcsrvname* è **sysname**, il valore predefinito è  **%** , che è l'unico valore che restituisce un set di risultati.  
  
 [  **@publisher_type** =] **'***publisher_type***' OUTPUT**  
 Tipo del server di pubblicazione. *publisher_type* è **sysname**, il valore predefinito è  **%** , che è l'unico valore che restituisce un set di risultati.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**server di distribuzione**|**sysname**|Nome del server di distribuzione.|  
|**database di distribuzione**|**sysname**|Nome del database di distribuzione.|  
|**Directory**|**nvarchar(255)**|Nome della directory di lavoro.|  
|**account**|**nvarchar(255)**|Nome dell'account utente di Windows.|  
|**conservazione distrib min**|**int**|Periodo di memorizzazione minimo per la distribuzione.|  
|**conservazione distrib max**|**int**|Periodo di memorizzazione massimo per la distribuzione.|  
|**periodo di memorizzazione cronologia**|**int**|Periodo di memorizzazione per la cronologia.|  
|**agente di pulizia della cronologia**|**nvarchar (100)**|Nome dell'agente di pulizia del contenuto della cronologia.|  
|**agente di pulizia di distribuzione**|**nvarchar (100)**|Nome dell'agente di pulizia dei riferimenti alla distribuzione.|  
|**nome del server RPC**|**sysname**|Nome del server di distribuzione remoto o locale.|  
|**nome di account di accesso RPC**|**sysname**|Account di accesso utilizzato per le chiamate di procedure remote al server di distribuzione remoto.|  
|**tipo di server di pubblicazione**|**sysname**|Tipo di server di pubblicazione. Può essere uno dei tipi seguenti:<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpdistributor** viene utilizzata in tutti i tipi di replica.  
  
 Se vengono specificati uno o più parametri di output durante l'esecuzione **sp_helpdistributor**, tutti i parametri di output, impostati su NULL vengono assegnati valori in uscita e non viene restituito alcun set di risultati. Se non viene specificato alcun parametro di output, viene restituito un set di risultati.  
  
## <a name="permissions"></a>Permissions  
 Il seguenti set di risultati le colonne o parametri di output vengono restituiti ai membri del **sysadmin** ruolo predefinito del server nel server di pubblicazione e **db_owner** ruolo predefinito del database nel database di pubblicazione:  
  
|Colonna del set di risultati|Parametro di output|  
|-----------------------|----------------------|  
|account|**@account**|  
|min distrib retention|**@min_distretention**|  
|max distrib retention|**@max_distretention**|  
|history retention|**@history_retention**|  
|history cleanup agent|**@history_cleanupagent**|  
|distribution cleanup agent|**@distrib_cleanupagent**|  
|rpc login name|none|  
  
 La colonna del set dei risultati seguente viene restituita agli utenti nell'elenco di accesso alla pubblicazione per una pubblicazione nel server di distribuzione:  
  
-   directory  
  
 Le seguenti colonne del set di risultati vengono restituite a tutti gli utenti.  
  
|Colonna del set di risultati|Parametro di output|  
|-----------------------|----------------------|  
|distributor|**@distributor**|  
|database di distribuzione|**@distribdb**|  
|rpc server name|**@rpcsrvname**|  
|publisher type|**@publisher_type**|  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
