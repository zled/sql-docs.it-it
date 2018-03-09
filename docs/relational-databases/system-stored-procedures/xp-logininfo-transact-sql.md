---
title: xp_logininfo (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xp_logininfo_TSQL
- xp_logininfo
dev_langs:
- TSQL
helpviewer_keywords:
- xp_logininfo
ms.assetid: ee7162b5-e11f-4a0e-a09c-1878814dbbbd
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b77eb07126cc739908713d8172695db9098d20d9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="xplogininfo-transact-sql"></a>xp_logininfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni su utenti e gruppi di Windows.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
xp_logininfo [ [ @acctname = ] 'account_name' ]   
     [ , [ @option = ] 'all' | 'members' ]   
     [ , [ @privilege = ] variable_name OUTPUT]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@acctname =** ] **'***account_name***'**  
 Nome di un utente o di un gruppo di Windows a cui è stato concesso l'accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *account_name* è **sysname**, con un valore predefinito è NULL. Se *account_name* non viene specificato, tutti i gruppi di Windows e gli utenti di Windows che sono stati esplicitamente concessa l'autorizzazione di accesso vengono segnalati. *account_name* deve essere completo. ad esempio ADVWKS4\macraes o BUILTIN\Administrators.  
  
 **'tutte'** | **'membri'**  
 Specifica se devono essere restituite informazioni su tutti i percorsi di autorizzazione per l'account oppure sui membri del gruppo di Windows. **@option**è **varchar (10)**, con un valore predefinito è NULL. A meno che non **tutti** viene specificato, viene visualizzato solo il primo percorso di autorizzazione.  
  
 [  **@privilege =** ] *nome_variabile*  
 Parametro di output tramite cui viene restituito il livello di privilegio dell'account di Windows specificato. *nome_variabile* è **varchar (10)**, con valore predefinito è 'Not wanted'. Il livello di privilegio restituito è **utente**, **admin**, o **null**.  
  
 OUTPUT  
 Quando specificato, viene inserita *nome_variabile* nel parametro di output.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**nome dell'account**|**sysname**|Nome completo dell'account di Windows.|  
|**tipo**|**Char(8)**|Tipo di account di Windows. I valori validi sono **utente** o **gruppo**.|  
|**con privilegi**|**Char(9)**|Privilegio di accesso per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I valori validi sono **admin**, **utente**, o **null**.|  
|**nome di accesso mappato**|**sysname**|Per gli account utente con privilegi utente, **nome account di accesso mappato** mostra che il nome di accesso mappato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tenta di utilizzare quando si accede con questo account utilizzando le regole mappate con il nome di dominio aggiunto prima di esso.|  
|**percorso di autorizzazione**|**sysname**|Appartenenza al gruppo che ha permesso all'account di ottenere l'accesso.|  
  
## <a name="remarks"></a>Osservazioni  
 Se *account_name* è specificato, **xp_logininfo** segnala il massimo livello di privilegio dell'utente di Windows specificato o del gruppo. Se un utente di Windows può accedere sia come amministratore di sistema che come utente di dominio, verrà restituito come amministratore di sistema. Se l'utente è membro di più gruppi di Windows con livello di privilegio uguale, viene restituito soltanto il gruppo a cui è stato concesso per primo l'accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se *account_name* è un utente di Windows valido o un gruppo che non è associato un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso, viene restituito un set di risultati vuoto. Se *account_name* non possono essere identificati come un utente di Windows valido o un gruppo, viene restituito un messaggio di errore.  
  
 Se *account_name* e **tutti** sono specificate, vengono restituiti tutti i percorsi di autorizzazione per l'utente di Windows o il gruppo. Se *account_name* è un membro di più gruppi, ognuno dei quali stato concesso l'accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vengono restituite più righe. Il **admin** vengono restituite le righe di privilegio prima di **utente** privilegio righe e all'interno di un privilegio di righe al livello vengono restituite nell'ordine in cui corrispondente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono stati creati account di accesso.  
  
 Se *account_name* e **membri** sono specificato, viene restituito un elenco dei membri del gruppo di livello successivo. Se *account_name* è un gruppo locale, l'elenco può includere utenti locali, gli utenti del dominio e gruppi. Se *account_name* è un account di dominio, l'elenco è costituito da utenti del dominio. Per recuperare informazioni sull'appartenenza ai gruppi, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere connesso al controller di dominio. Se il server non può contenere il controller di dominio, non verranno restituite informazioni.  
  
 **xp_logininfo** restituisce solo informazioni dai gruppi globali di Active Directory, non dai gruppi universali.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza di **sysadmin** ruolo del server o l'appartenenza al **pubblica** ruolo predefinito del database nel **master** database con l'autorizzazione EXECUTE.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono visualizzate informazioni sul gruppo di Windows `BUILTIN\Administrators`.  
  
```  
EXEC xp_logininfo 'BUILTIN\Administrators';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Estese generali Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  
