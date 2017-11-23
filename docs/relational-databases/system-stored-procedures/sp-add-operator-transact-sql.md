---
title: sp_add_operator (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2016
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
- sp_add_operator
- sp_add_operator_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_add_operator
ms.assetid: 817cd98a-4dff-4ed8-a546-f336c144d1e0
caps.latest.revision: "26"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cc0807d00d85fcdb9f41d4cf13b696bff7566d7a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="spaddoperator-transact-sql"></a>sp_add_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un operatore (destinatario delle notifiche) da utilizzare con avvisi e processi.  
  
 
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_operator [ @name = ] 'name'   
     [ , [ @enabled = ] enabled ]   
     [ , [ @email_address = ] 'email_address' ]   
     [ , [ @pager_address = ] 'pager_address' ]   
     [ , [ @weekday_pager_start_time = ] weekday_pager_start_time ]   
     [ , [ @weekday_pager_end_time = ] weekday_pager_end_time ]   
     [ , [ @saturday_pager_start_time = ] saturday_pager_start_time ]   
     [ , [ @saturday_pager_end_time = ] saturday_pager_end_time ]   
     [ , [ @sunday_pager_start_time = ] sunday_pager_start_time ]   
     [ , [ @sunday_pager_end_time = ] sunday_pager_end_time ]   
     [ , [ @pager_days = ] pager_days ]   
     [ , [ @netsend_address = ] 'netsend_address' ]   
     [ , [ @category_name = ] 'category' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@name=** ] **'***nome***'**  
 Nome di un operatore (destinatario della notifica). Questo nome deve essere univoco e non può contenere la percentuale (**%**) caratteri. *nome* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@enabled=** ] *abilitato*  
 Indica lo stato corrente dell'operatore. *abilitato* è **tinyint**, il valore predefinito è **1** (abilitato). Se **0**, l'operatore non è abilitato e non riceve notifiche.  
  
 [  **@email_address=** ] **'***email_address***'**  
 Indirizzo di posta elettronica dell'operatore. Questa stringa viene passata direttamente al sistema di posta elettronica. *email_address* è **nvarchar (100)**, con un valore predefinito è NULL.  
  
 È possibile specificare un indirizzo di posta elettronica fisico o un alias per *email_address*. Esempio:  
  
 '**jdoe**'o'**jdoe@xyz.com**'  
  
> [!NOTE]  
>  È necessario utilizzare l'indirizzo di posta elettronica per Posta elettronica database.  
  
 [  **@pager_address=** ] **'***pager_address***'**  
 Indirizzo del cercapersone dell'operatore. Questa stringa viene passata direttamente al sistema di posta elettronica. *pager_address* è **narchar(100)**, con un valore predefinito è NULL.  
  
 [  **@weekday_pager_start_time=** ] *weekday_pager_start_time*  
 Data e ora successivamente alle quali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent invia notifica tramite cercapersone all'operatore specificato nei giorni della settimana, dal lunedì al venerdì. *weekday_pager_start_time*è **int**, il valore predefinito è **090000**, che indica le 9.00 nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [  **@weekday_pager_end_time=** ] *weekday_pager_end_time*  
 Il tempo trascorso il quale **SQLServerAgent** servizio non invia notifiche al cercapersone dell'operatore specificato giorni feriali da lunedì a venerdì. *weekday_pager_end_time*è **int**, il valore predefinito è 180000, che indica le 18.00 nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [  **@saturday_pager_start_time =**] *saturday_pager_start_time*  
 Il tempo trascorso il quale **SQLServerAgent** servizio invia notifiche al cercapersone dell'operatore specificato sabato. *saturday_pager_start_time* è **int**, il valore predefinito è 090000, che indica le 9.00 nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [  **@saturday_pager_end_time=** ] *saturday_pager_end_time*  
 Il tempo trascorso il quale **SQLServerAgent** servizio non invia notifiche al cercapersone dell'operatore specificato sabato. *saturday_pager_end_time*è **int**, il valore predefinito è **180000**, ovvero le 18.00 nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [  **@sunday_pager_start_time=** ] *sunday_pager_start_time*  
 Il tempo trascorso il quale **SQLServerAgent** servizio invia notifiche al cercapersone dell'operatore specificato domenica. *sunday_pager_start_time*è **int**, il valore predefinito è **090000**, che indica le 9.00 nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [  **@sunday_pager_end_time =**] *sunday_pager_end_time*  
 Il tempo trascorso il quale **SQLServerAgent** servizio non invia notifiche al cercapersone dell'operatore specificato domenica. *sunday_pager_end_time*è **int**, il valore predefinito è **180000**, ovvero le 18.00 nel formato a 24 ore e deve essere immesso nel formato HHMMSS.  
  
 [  **@pager_days=** ] *pager_days*  
 Numero che indica i giorni in cui l'operatore può essere rintracciato tramite cercapersone (in base all'ora di inizio e di fine specificate). *pager_days*è **tinyint**, il valore predefinito è **0** che indica che l'operatore non è mai disponibile per la ricezione di una pagina. I valori validi sono da **0** tramite **127**. *pager_days*viene calcolato sommando i singoli valori dei giorni necessari. Ad esempio, da lunedì a venerdì è **2**+**4**+**8**+**16** + **32** = **62**. Nella tabella seguente vengono elencati i valori disponibili per ogni giorno della settimana.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**1**|Domenica|  
|**2**|Lunedì|  
|**4**|Martedì|  
|**8**|Mercoledì|  
|**16**|Giovedì|  
|**32**|Venerdì|  
|**64**|Sabato|  
  
 [  **@netsend_address=** ] **'***netsend_address***'**  
 Indirizzo di rete dell'operatore a cui viene inviato il messaggio di rete. *netsend_address*è **nvarchar (100)**, con un valore predefinito è NULL.  
  
 [  **@category_name=** ] **'***categoria***'**  
 Nome della categoria per questo operatore. *categoria* è **sysname**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_add_operator** deve essere eseguita la **msdb** database.  
  
 L'invio di messaggi sul cercapersone è supportato dal sistema di posta elettronica, in cui deve essere disponibile la funzionalità per il trasferimento di messaggi su cercapersone.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è incluso un semplice strumento grafico per la gestione dei processi, che è lo strumento consigliato per la creazione e la gestione dell'infrastruttura dei processi.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_add_operator**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono impostate e attivate le informazioni per l'operatore `danwi`. L'operatore è abilitato. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent invia notifiche tramite cercapersone da lunedì a venerdì, dalle 8.00 alle 17.00.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_operator  
    @name = N'Dan Wilson',  
    @enabled = 1,  
    @email_address = N'danwi',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 62 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_delete_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_help_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_operator &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-operator-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
