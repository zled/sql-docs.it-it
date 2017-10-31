---
title: ALTER SERVICE (Transact-SQL) | Documenti Microsoft
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
- ALTER SERVICE
- ALTER_SERVICE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- modifying services
- contracts [Service Broker], modifying
- ALTER SERVICE statement
- services [Service Broker], modifying
ms.assetid: 2b4608f7-bb2e-4246-aa29-b52c55995b3a
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f0f09a018648566cd928258da958bb06dedc6022
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-service-transact-sql"></a>ALTER SERVICE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica un servizio esistente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER SERVICE service_name   
   [ ON QUEUE [ schema_name . ]queue_name ]   
   [ ( < opt_arg > [ , ...n ] ) ]  
[ ; ]  
  
<opt_arg> ::=  
   ADD CONTRACT contract_name | DROP CONTRACT contract_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *SERVICE_NAME*  
 Nome del servizio da modificare. Non è possibile specificare i nomi del server, del database e dello schema.  
  
 CODA ON [ *schema_name***.** ] *nome_coda*  
 Specifica la nuova coda per questo servizio. [!INCLUDE[ssSB](../../includes/sssb-md.md)] sposta tutti i messaggi per questo servizio dalla coda corrente alla nuova coda.  
  
 Aggiungi contratto *contract_name*  
 Specifica un contratto da aggiungere al set dei contratti esposti da questo servizio.  
  
 DROP CONTRACT *contract_name*  
 Specifica un contratto da eliminare dal set dei contratti esposti da questo servizio. [!INCLUDE[ssSB](../../includes/sssb-md.md)] invia un messaggio di errore per tutte le conversazioni esistenti con il servizio che utilizzano questo contratto.  
  
## <a name="remarks"></a>Osservazioni  
 Quando l'istruzione ALTER SERVICE elimina un contratto da un servizio, il servizio non può più essere la destinazione per le conversazioni che utilizzano tale contratto. [!INCLUDE[ssSB](../../includes/sssb-md.md)] non consente pertanto nuove conversazioni con il servizio in base a quel contratto. Le conversazioni esistenti che utilizzano il contratto non subiscono variazioni.  
  
 Per modificare il parametro AUTHORIZATION per un servizio, utilizzare l'istruzione ALTER AUTHORIZATION.  
  
## <a name="permissions"></a>Permissions  
 L'autorizzazione per modificare un servizio viene impostato sul proprietario del servizio, i membri del **db_ddladmin** o **db_owner** fissa ruoli del database e i membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-queue-for-a-service"></a>A. Modifica della coda per un servizio  
 Nell'esempio seguente il servizio `//Adventure-Works.com/Expenses` viene modificato in modo che utilizzi la coda `NewQueue`.  
  
```  
ALTER SERVICE [//Adventure-Works.com/Expenses]  
    ON QUEUE NewQueue ;  
```  
  
### <a name="b-adding-a-new-contract-to-the-service"></a>B. Aggiunta di un nuovo contratto al servizio  
 Nell'esempio seguente il servizio `//Adventure-Works.com/Expenses` viene modificato in modo da consentire i dialoghi nel contratto `//Adventure-Works.com/Expenses`.  
  
```  
ALTER SERVICE [//Adventure-Works.com/Expenses]  
    (ADD CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]) ;  
```  
  
### <a name="c-adding-a-new-contract-to-the-service-dropping-existing-contract"></a>C. Aggiunta di un nuovo contratto al servizio, eliminazione del contratto esistente  
 Nell'esempio seguente il servizio `//Adventure-Works.com/Expenses` viene modificato in modo da consentire i dialoghi nel contratto `//Adventure-Works.com/Expenses/ExpenseProcessing` e da non consentire i dialoghi nel contratto `//Adventure-Works.com/Expenses/ExpenseSubmission`.  
  
```  
ALTER SERVICE [//Adventure-Works.com/Expenses]  
    (ADD CONTRACT [//Adventure-Works.com/Expenses/ExpenseProcessing],   
     DROP CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]) ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SERVICE &#40;Transact-SQL&#41;](../../t-sql/statements/create-service-transact-sql.md)   
 [ELIMINARE servizio &#40; Transact-SQL &#41;](../../t-sql/statements/drop-service-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

