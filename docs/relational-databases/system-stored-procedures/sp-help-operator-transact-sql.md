---
title: sp_help_operator (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_operator
- sp_help_operator_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_operator
ms.assetid: caedc43d-44b8-415a-897e-92923f6de3b8
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 392586d2f3ea34b6914cb7bf34757d0481e890a9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpoperator-transact-sql"></a>sp_help_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sugli operatori definiti per il server.  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_operator  
     { [ @operator_name = ] 'operator_name'   
     | [ @operator_id = ] operator_id }  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@operator_name=** ] **'***operator_name***'**  
 Nome dell'operatore. *operator_name* è **sysname**. Se *operator_name* viene omesso, vengono restituite informazioni su tutti gli operatori.  
  
 [  **@operator_id=** ] *operator_id*  
 Numero di identificazione dell'operatore su cui vengono richieste informazioni. *operator_id*è **int**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *operator_id* o *operator_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Numero di identificazione dell'operatore.|  
|**name**|**sysname**|Nome dell'operatore.|  
|**abilitato**|**tinyint**|Specifica se l'operatore è disponibile per la ricezione di notifiche:<br /><br /> **1** = Sì<br /><br /> **0** = No|  
|**email_address**|**nvarchar (100)**|Indirizzo di posta elettronica dell'operatore.|  
|**last_email_date**|**int**|Data dell'ultima notifica dell'operatore tramite posta elettronica.|  
|**last_email_time**|**int**|Ora dell'ultima notifica dell'operatore tramite posta elettronica.|  
|**pager_address**|**nvarchar (100)**|Indirizzo cercapersone dell'operatore.|  
|**last_pager_date**|**int**|Data dell'ultima notifica dell'operatore tramite cercapersone.|  
|**last_pager_time**|**int**|Ora dell'ultima notifica dell'operatore tramite cercapersone.|  
|**weekday_pager_start_time**|**int**|Inizio del periodo di tempo durante il quale l'operatore è disponibile per ricevere notifiche tramite cercapersone in un giorno feriale.|  
|**weekday_pager_end_time**|**int**|Termine del periodo di tempo durante il quale l'operatore è disponibile per ricevere notifiche tramite cercapersone in un giorno feriale|  
|**saturday_pager_start_time**|**int**|Inizio del periodo di tempo durante il quale l'operatore è disponibile per ricevere notifiche tramite cercapersone il sabato.|  
|**saturday_pager_end_time**|**int**|Termine del periodo di tempo durante il quale l'operatore è disponibile per ricevere notifiche tramite cercapersone il sabato.|  
|**sunday_pager_start_time**|**int**|Inizio del periodo di tempo durante il quale l'operatore è disponibile per ricevere notifiche tramite cercapersone la domenica.|  
|**sunday_pager_end_time**|**int**|Termine del periodo di tempo durante il quale l'operatore è disponibile per ricevere notifiche tramite cercapersone la domenica.|  
|**pager_days**|**tinyint**|Maschera di bit (**1** = domenica, **64** = sabato) di giorni-della settimana che indica quando l'operatore è disponibile per ricevere notifiche tramite cercapersone.|  
|**netsend_address**|**nvarchar (100)**|Indirizzo dell'operatore per le notifiche dei messaggi popup di rete.|  
|**last_netsend_date**|**int**|Data dell'ultima notifica inviata all'operatore tramite un messaggio popup di rete.|  
|**last_netsend_time**|**int**|Ora dell'ultima notifica inviata all'operatore tramite un messaggio popup di rete.|  
|**category_name**|**sysname**|Nome della categoria a cui appartiene l'operatore.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_operator** deve essere eseguita la **msdb** database.  
  
## <a name="permissions"></a>Permissions  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sull'operatore `François Ajenstat`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_operator  
    @operator_name = N'François Ajenstat' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_update_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
