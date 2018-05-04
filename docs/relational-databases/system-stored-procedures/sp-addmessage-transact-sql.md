---
title: sp_addmessage (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addmessage
- sp_addmessage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addmessage
ms.assetid: 54746d30-f944-40e5-a707-f2d9be0fb9eb
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 05769a0a060de4a78bdcf425e20d004ef9ae9099
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spaddmessage-transact-sql"></a>sp_addmessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia un nuovo messaggio di errore definito dall'utente in un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. I messaggi archiviati tramite **sp_addmessage** possono essere visualizzati utilizzando il **Sys. Messages** vista del catalogo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addmessage [ @msgnum= ] msg_id , [ @severity= ] severity , [ @msgtext= ] 'msg'   
     [ , [ @lang= ] 'language' ]   
     [ , [ @with_log= ] { 'TRUE' | 'FALSE' } ]   
     [ , [ @replace= ] 'replace' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@msgnum****=** ] *msg_id*  
 ID del messaggio. *msg_id* viene **int** con un valore predefinito è NULL. *msg_id* per errore definiti dall'utente dei messaggi possono essere un numero intero compreso tra 50.001 e 2.147.483.647. La combinazione di *msg_id* e *language* devono essere univoci; se l'ID esiste già per la lingua specificata, viene restituito un errore.  
  
 [  **@severity =** ]*gravità*  
 Livello di gravità dell'errore. *livello di gravità* viene **smallint** con un valore predefinito è NULL. I livelli validi sono compresi tra 1 e 25. Per altre informazioni sui livelli di gravità, vedere [Gravità degli errori del Motore di database](../../relational-databases/errors-events/database-engine-error-severities.md).  
  
 [ **@msgtext =** ] **'***msg***'**  
 Testo del messaggio di errore. *MSG* viene **nvarchar(255** con un valore predefinito è NULL.  
  
 [  **@lang =** ] **'***language***'**  
 Lingua del messaggio. *linguaggio* viene **sysname** con un valore predefinito è NULL. Poiché nello stesso server, è possono installare più lingue *language* specifica la lingua in cui viene scritto ogni messaggio. Quando *language* viene omesso, la lingua è la lingua predefinita per la sessione.  
  
 [  **@with_log =** ] { **'** TRUE **'** | **'FALSE'** }  
 Indica se il messaggio deve essere scritto nel registro applicazioni di Windows quando si verifica l'errore. **@with_log** viene **varchar (5)** con un valore predefinito è FALSE. Se è TRUE, l'errore viene sempre scritto nel registro applicazioni di Windows. Se è FALSE, l'errore viene scritto nel registro applicazioni di Windows a seconda della modalità con cui è stato generato. Solo i membri del **sysadmin** ruolo del server è possibile utilizzare questa opzione.  
  
> [!NOTE]  
>  Se un messaggio viene scritto nel registro applicazioni di Windows, viene registrato inoltre nel file di log degli errori di [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 [ **@replace** *=* ] **'***Sostituisci***'**  
 Se specificato come stringa *sostituire*, un messaggio di errore esistente viene sovrascritto con livello di gravità e di testo messaggio nuovo. *Sostituire* viene **varchar(7)** con un valore predefinito è NULL. Questa opzione deve essere specificata se *msg_id* esiste già. Se viene sostituito un messaggio in inglese Messaggio in lingua inglese, il livello di gravità viene sostituito per tutti i messaggi in tutte le lingue che presentano lo stesso *msg_id*.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Per le versioni non in lingua inglese di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è necessario che un messaggio sia disponibile nella versione inglese (Stati Uniti) per poterlo aggiungere in un'altra lingua. La gravità delle due versioni del messaggio devono corrispondere.  
  
 Quando vengono localizzati messaggi che includono parametri, utilizzare i numeri di parametro che corrispondono ai parametri del messaggio originale e inserire un punto esclamativo (!) dopo ogni numero di parametro.  
  
|Messaggio originale|Messaggio localizzato|  
|----------------------|-----------------------|  
|'Original message param 1: %s,<br /><br /> param 2: %d'|'Messaggio localizzato param 1: %1!<br /><br /> param 2: %2!'|  
  
 A causa delle differenze nella sintassi delle varie lingue, i numeri di parametro nel messaggio localizzato potrebbero non essere nella stessa sequenza del messaggio originale.  
  
## <a name="permissions"></a>Autorizzazioni  
È richiesta l'appartenenza di **sysadmin** o **serveradmin** ruoli predefiniti del server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-defining-a-custom-message"></a>A. Definizione di un messaggio personalizzato  
 Nell'esempio seguente aggiunge un messaggio personalizzato a **Sys. Messages**.  
  
```  
USE master;  
GO  
EXEC sp_addmessage 50001, 16,   
   N'Percentage expects a value between 20 and 100.   
   Please reexecute with a more appropriate value.';  
GO  
```  
  
### <a name="b-adding-a-message-in-two-languages"></a>B. Aggiunta di un messaggio in due lingue  
 Nell'esempio seguente viene innanzitutto aggiunto un messaggio in inglese (Stati Uniti) e quindi viene aggiunto lo stesso messaggio in francese`.`  
  
```  
USE master;  
GO  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'The item named %s already exists in %s.',   
   @lang = 'us_english';  
  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'L''élément nommé %1! existe déjà dans %2!',   
   @lang = 'French';  
GO  
```  
  
### <a name="c-changing-the-order-of-parameters"></a>C. Modifica dell'ordine dei parametri  
 Nell'esempio seguente viene innanzitutto aggiunto un messaggio in inglese (Stati Uniti) e quindi viene aggiunto un messaggio localizzato in cui è stato modificato l'ordine dei parametri.  
  
```  
USE master;  
GO  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        N'This is a test message with one numeric  
        parameter (%d), one string parameter (%s),   
        and another string parameter (%s).',  
    @lang = 'us_english';  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        -- In the localized version of the message,  
        -- the parameter order has changed. The   
        -- string parameters are first and second  
        -- place in the message, and the numeric   
        -- parameter is third place.  
        N'Dies ist eine Testmeldung mit einem   
        Zeichenfolgenparameter (%3!),  
        einem weiteren Zeichenfolgenparameter (%2!),   
        und einem numerischen Parameter (%1!).',  
    @lang = 'German';  
GO    
  
-- Changing the session language to use the U.S. English  
-- version of the error message.  
SET LANGUAGE us_english;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2') -- error, severity, state,  
GO                                       -- parameters.  
  
-- Changing the session language to use the German  
-- version of the error message.  
SET LANGUAGE German;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2'); -- error, severity, state,   
GO                                       -- parameters.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
