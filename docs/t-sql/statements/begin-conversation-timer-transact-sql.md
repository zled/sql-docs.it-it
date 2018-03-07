---
title: BEGIN CONVERSATION TIMER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONVERSATION
- BEGIN_CONVERSATION_TSQL
- TIMER_TSQL
- TIMER
- CONVERSATION TIMER
- CONVERSATION_TIMER_TSQL
- BEGIN CONVERSATION TIMER
- BEGIN_CONVERSATION_TIMER_TSQL
- CONVERSATION_TSQL
- BEGIN CONVERSATION
dev_langs:
- TSQL
helpviewer_keywords:
- BEGIN CONVERSATION TIMER statement
- DialogTimer message
- dialogs [Service Broker], beginning
- timeouts [Service Broker]
- timer messages [Service Broker]
- conversations [Service Broker], timers
- starting timers [Service Broker]
- http://schemas.microsoft.com/SQL/ServiceBroker/DialogTimer message
ms.assetid: 98e49b3f-a38f-4180-8171-fa9cb30db4cb
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f85695e3d8263936d053979074a92b52fba7259
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="begin-conversation-timer-transact-sql"></a>BEGIN CONVERSATION TIMER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Avvia un timer. Quando il timeout scade, [!INCLUDE[ssSB](../../includes/sssb-md.md)] inserisce un messaggio di tipo `http://schemas.microsoft.com/SQL/ServiceBroker/DialogTimer` nella coda locale per la conversazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BEGIN CONVERSATION TIMER ( conversation_handle )  
   TIMEOUT = timeout   
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 BEGIN CONVERSATION TIMER **(***conversation_handle***)**  
 Specifica la conversazione per cui avviare il timer. Il *conversation_handle* deve essere di tipo **uniqueidentifier**.  
  
 TIMEOUT  
 Specifica, in secondi, quanto tempo deve trascorrere prima che il messaggio venga inserito nella coda.  
  
## <a name="remarks"></a>Osservazioni  
 Il timer di conversazione consente a un'applicazione di ricevere un messaggio per una conversazione dopo un periodo di tempo specifico. Se si chiama BEGIN CONVERSATION TIMER per una conversazione prima della scadenza del timer, per il timeout verrà impostato il nuovo valore. A differenza di quanto avviene per la durata della conversazione, ogni lato della conversazione ha un timer indipendente. Il **DialogTimer** messaggio arriva nella coda locale senza modificare il lato remoto della conversazione. Un'applicazione può, quindi, utilizzare un messaggio timer per qualsiasi motivo.  
  
 È possibile, ad esempio, utilizzare il timer di conversazione per evitare che un'applicazione attenda troppo a lungo una risposta scaduta. Se si prevede che un'applicazione completi un dialogo in 30 secondi, è possibile impostare il timer di conversazione per tale dialogo su 60 secondi (30 secondi più altri 30 secondi di tolleranza). Se il dialogo è ancora aperto dopo 60 secondi, l'applicazione riceve un messaggio di timeout nella coda.  
  
 In alternativa un'applicazione può utilizzare un timer di conversazione per richiedere l'attivazione in un determinato momento. Si potrebbe, ad esempio, creare un servizio che segnali il numero di connessioni attive a intervalli di pochi minuti oppure un servizio che segnali il numero di ordini di acquisto aperti ogni sera. Il servizio viene impostato un timer di conversazione in modo che scada sul tempo desiderato; Quando il timer scade, [!INCLUDE[ssSB](../../includes/sssb-md.md)] invia un **DialogTimer** messaggio. Il **DialogTimer** messaggio cause [!INCLUDE[ssSB](../../includes/sssb-md.md)] per avviare l'attivazione stored procedure per la coda. La stored procedure invia un messaggio al servizio remoto e riavvia il timer di conversazione.  
  
 BEGIN CONVERSATION TIMER non è valida in una funzione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Autorizzazione per l'impostazione di un timer di conversazione valori predefiniti per gli utenti che dispongono delle autorizzazioni SEND sul servizio per la conversazione, i membri del **sysadmin** risolto ruolo del server e i membri del **db_owner** ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene impostato un timeout di due minuti per il dialogo identificato da `@dialog_handle`.  
  
```  
-- @dialog_handle is of type uniqueidentifier and  
-- contains a valid conversation handle.  
  
BEGIN CONVERSATION TIMER (@dialog_handle)  
TIMEOUT = 120 ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [END CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [RECEIVE &#40;Transact-SQL&#41;](../../t-sql/statements/receive-transact-sql.md)  
  
  
