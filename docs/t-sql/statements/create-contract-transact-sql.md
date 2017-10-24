---
title: CREARE il contratto (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTRACT_TSQL
- CREATE_CONTRACT_TSQL
- CREATE CONTRACT
- CONTRACT
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE CONTRACT statement
- contracts [Service Broker], creating
- message types [Service Broker], contracts
ms.assetid: 494cbfa6-8e93-4161-a64d-90d681915211
caps.latest.revision: 48
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 962ce2d6568a597bd580f7fc9bcd2e9243e44dc4
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-contract-transact-sql"></a>CREATE CONTRACT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un nuovo contratto. Un contratto definisce i tipi di messaggio utilizzati in una conversazione di [!INCLUDE[ssSB](../../includes/sssb-md.md)], nonché il lato della conversazione che può inviare messaggi di tale tipo. Ogni conversazione viene eseguita in base a un contratto. Il servizio di origine specifica il contratto per la conversazione all'avvio della conversazione stessa, mentre il servizio Target specifica i contratti accettati per le conversazioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE CONTRACT contract_name  
   [ AUTHORIZATION owner_name ]  
      (  {   { message_type_name | [ DEFAULT ] }  
          SENT BY { INITIATOR | TARGET | ANY }   
       } [ ,...n] )   
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *contract_name*  
 Nome del contratto da creare. Il nuovo contratto viene creato nel database corrente e diventa di proprietà dell'identità specificata nella clausola AUTHORIZATION. Non è possibile specificare i nomi del server, del database e dello schema. Il *contract_name* può contenere fino a 128 caratteri.  
  
> [!NOTE]  
>  Non creare un contratto che utilizza la parola chiave ANY per il *contract_name*. Quando si specifica ANY per un nome del contratto in CREATE BROKER PRIORITY, la priorità viene considerata per tutti i contratti e non è limitata a un contratto il cui nome è ANY.  
  
 AUTORIZZAZIONE *owner_name*  
 Imposta come proprietario del contratto l'utente o il ruolo del database specificato. Quando l'utente corrente è **dbo** o **sa**, *owner_name* può essere il nome di qualsiasi utente o ruolo valido. In caso contrario, *owner_name* deve essere il nome dell'utente corrente, il nome di un utente che l'utente corrente dispone delle autorizzazioni di rappresentazione o il nome di un ruolo a cui appartiene l'utente corrente. Se la clausola viene omessa, il contratto appartiene all'utente corrente.  
  
 *message_type_name*  
 Nome del tipo di messaggio da includere nel contratto.  
  
 SENT BY  
 Specifica l'endpoint che può inviare un messaggio del tipo indicato. I contratti documentano i messaggi che i servizi possono utilizzare per eseguire conversazioni specifiche. Ogni conversazione presenta due endpoint: il *iniziatore* endpoint, il servizio che ha avviato la conversazione, e *destinazione* endpoint, il servizio che sta contattando l'iniziatore.  
  
 INITIATOR  
 Indica che solo l'endpoint initiator della conversazione può inviare messaggi del tipo specificato. Un servizio che avvia una conversazione è definito come il *iniziatore* della conversazione.  
  
 TARGET  
 Indica che solo l'endpoint target della conversazione può inviare messaggi del tipo specificato. Un servizio che accetta una conversazione avviata da un altro servizio è definito come il *destinazione* della conversazione.  
  
 ANY  
 Indica che i messaggi del tipo specificato possono essere inviati sia dal servizio initiator che dal servizio target.  
  
 [ DEFAULT ]  
 Indica che il contratto supporta messaggi del tipo predefinito. Per impostazione predefinita, tutti i database contengono un tipo di messaggio denominato DEFAULT. Questo tipo di messaggio utilizza la convalida di tipo NONE. Nel contesto di questa clausola DEFAULT non è una parola chiave ed è pertanto necessario delimitarlo come identificatore. In Microsoft SQL Server è inoltre disponibile un contratto DEFAULT che specifica il tipo di messaggio DEFAULT.  
  
## <a name="remarks"></a>Osservazioni  
 L'ordine dei tipi di messaggio nel contratto non è significativo. Dopo che il servizio di destinazione ha ricevuto il primo messaggio, [!INCLUDE[ssSB](../../includes/sssb-md.md)] consente ai lati della conversazione di inviare qualsiasi messaggio consentito al lato specifico della conversazione in qualsiasi momento. Ad esempio, se l'iniziatore della conversazione può inviare messaggi di tipo **//Adventure-Works.com/Expenses/SubmitExpense**, [!INCLUDE[ssSB](../../includes/sssb-md.md)] consente al servizio initiator di inviare un numero qualsiasi di **SubmitExpense**messaggi durante la conversazione.  
  
 In un contratto non è possibile modificare i tipi di messaggio e la direzione dei messaggi. Per modificare il parametro AUTHORIZATION per un contratto, utilizzare l'istruzione ALTER AUTHORIZATION.  
  
 Un contratto deve consentire al servizio initiator di inviare un messaggio. L'istruzione CREATE CONTRACT ha esito negativo se il contratto non include almeno un tipo di messaggio SENT BY ANY o SENT BY INITIATOR.  
  
 Indipendentemente dal contratto, un servizio può sempre ricevere i tipi di messaggio `http://schemas.microsoft.com/SQL/ServiceBroker/DialogTimer`, `http://schemas.microsoft.com/SQL/ServiceBroker/Error`, e `http://schemas.microsoft.com/SQL/ServiceBroker/EndDialog`. [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilizza questi tipi di messaggio per i messaggi di sistema all'applicazione.  
  
 Un contratto non può essere un oggetto temporaneo. Sono consentiti i nomi di contratto che iniziano con #, ma in questo caso si tratta di oggetti permanenti.  
  
## <a name="permissions"></a>Permissions  
 Per impostazione predefinita, i membri del **db_ddladmin** o **db_owner** ruoli predefiniti del database e **sysadmin** ruolo predefinito del server possono creare contratti.  
  
 Per impostazione predefinita, il proprietario del contratto, i membri del **db_ddladmin** o **db_owner** fissa ruoli del database e i membri del **sysadmin** ruolo predefinito del server con riferimenti l'autorizzazione per un contratto.  
  
 L'utente che esegue l'istruzione CREATE CONTRACT deve disporre dell'autorizzazione REFERENCES per tutti i tipi di messaggio specificati.  
  
## <a name="examples"></a>Esempi  
 **A. Creazione di un contratto**  
  
 Nell'esempio seguente viene creato un contratto per il rimborso spese in base a tre tipi di messaggio.  
  
```  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/SubmitExpense]           
    VALIDATION = WELL_FORMED_XML ;           
  
CREATE MESSAGE TYPE  
    [//Adventure-Works.com/Expenses/ExpenseApprovedOrDenied]           
    VALIDATION = WELL_FORMED_XML ;           
  
CREATE MESSAGE TYPE           
    [//Adventure-Works.com/Expenses/ExpenseReimbursed]           
    VALIDATION= WELL_FORMED_XML ;           
  
CREATE CONTRACT            
    [//Adventure-Works.com/Expenses/ExpenseSubmission]           
    ( [//Adventure-Works.com/Expenses/SubmitExpense]           
          SENT BY INITIATOR,           
      [//Adventure-Works.com/Expenses/ExpenseApprovedOrDenied]           
          SENT BY TARGET,           
      [//Adventure-Works.com/Expenses/ExpenseReimbursed]           
          SENT BY TARGET           
    ) ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ELIMINARE contratto &#40; Transact-SQL &#41;](../../t-sql/statements/drop-contract-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

