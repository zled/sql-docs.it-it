---
title: sp_helpreplicationdboption (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d53bf08bf26d8682093d72e55f290701d0b3c625
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpreplicationdboption-transact-sql"></a>sp_helpreplicationdboption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indica se i database nel server di pubblicazione sono abilitati per la replica. Questa stored procedure viene eseguita in qualsiasi database del server di pubblicazione. *Non è supportata per server di pubblicazione Oracle.*  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpreplicationdboption [ [ @dbname =] 'dbname' ]  
    [ , [ @type = ] 'type' ]  
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@dbname=**] **'***dbname***'**  
 Nome del database. *dbname* è **sysname**, il valore predefinito è  **%** . Se  **%** , il set di risultati contiene tutti i database nel server di pubblicazione, in caso contrario solo le informazioni nel database specificato viene quindi restituite. Non vengono restituite informazioni per gli eventuali database per cui l'utente non dispone delle autorizzazioni appropriate, come indicato di seguito.  
  
 [  **@type=**] **'***tipo***'**  
 Limita il set di risultati al database in cui l'opzione di replica specificato *tipo* valore è stato abilitato. *tipo* è **sysname**, e può essere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**pubblicazione**|È consentita la replica transazionale.|  
|**pubblicazione di tipo merge**|È consentita la replica di tipo merge.|  
|**è consentita la replica** (impostazione predefinita)|È consentita la replica transazionale o la replica di tipo merge.|  
  
 [  **@reserved=** ] *riservato*  
 Specifica se vengono restituite informazioni sulle pubblicazioni e sulle sottoscrizioni esistenti. *riservato* è **bit**, con un valore predefinito pari a 0. Se **1**, il set di risultati include informazioni su se il database specificato dispone di eventuali pubblicazioni o sottoscrizioni esistenti.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del database.|  
|**id**|**int**|Identificatore del database.|  
|**transpublish**|**bit**|Se il database è stato abilitato per una pubblicazione snapshot o transazionale; valore **1** indica che è abilitata la pubblicazione transazionale o snapshot.|  
|**mergepublish**|**bit**|Se il database è stato abilitato per l'unione di pubblicazione; valore **1** significa che la pubblicazione di tipo merge è abilitata.|  
|**dbowner**|**bit**|Se l'utente è membro il **db_owner** ruolo predefinito del database; valore **1** indica che l'utente è un membro di questo ruolo.|  
|**dbReadOnly**|**bit**|È se il database viene contrassegnato come di sola lettura. valore **1** significa che il database è di sola lettura.|  
|**haspublications**|**bit**|Se il database dispone di pubblicazioni esistenti valore **1** vi sono pubblicazioni esistenti.|  
|**haspullsubscriptions**|**bit**|È il database con le sottoscrizioni pull esistenti; valore **1** significa che sono presenti sottoscrizioni pull.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpreplicationdboption** viene utilizzata in repliche snapshot, transazionali e di tipo merge.  
  
## <a name="permissions"></a>Permissions  
 I membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_helpreplicationdboption** per qualsiasi database. I membri del **db_owner** ruolo predefinito del database possono eseguire **sp_helpreplicationdboption** per quel database.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_replicationdboption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
