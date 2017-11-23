---
title: sp_get_redirected_publisher (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- sp_get_redirected_publisher_TSQL
- sp_get_redirected_publisher
ms.assetid: d47a9ab5-f2cc-42a8-8be9-a33895ce44f0
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cdd0079a3af3ae647c66ea7106e79fb6f9a93ef9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spgetredirectedpublisher-transact-sql"></a>sp_get_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Utilizzato dagli agenti di replica per eseguire una query su un database di distribuzione in modo da determinare se è stato reindirizzato il server di pubblicazione originale.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_get_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @bypass_publisher_validation = ] [0 | 1 ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@original_publisher**  =] **'***original_publisher***'**  
 Il nome del database da pubblicare. *publisher_db* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db**  =] **'***publisher_db***'**  
 Il nome del database da pubblicare. *publisher_db* è **sysname**, non prevede alcun valore predefinito.  
  
 [ **@bypass_publisher_validation** = ] [0 | 1 ]  
 Utilizzato per ignorare la convalida del server di pubblicazione reindirizzato. Se è 0, viene eseguita la convalida. Se pari a 1, non viene eseguita la convalida. *bypass_publisher_validation* è **bit**, con un valore predefinito è 0.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**redirected_publisher**|**sysname**|Il nome del server di pubblicazione dopo il reindirizzamento.|  
|**error_number**|**int**|Il numero dell'errore di convalida.|  
|**error_severity**|**int**|La gravità dell'errore di convalida.|  
|**error_message**|**nvarchar(4000)**|Il testo del messaggio di errore di convalida.|  
  
## <a name="remarks"></a>Osservazioni  
 *redirected_publisher* restituisce il nome del server di pubblicazione corrente. Restituisce null se il server di pubblicazione e database di pubblicazione non sono stati reindirizzati utilizzando **sp_redirect_publisher**.  
  
 Se non è richiesta la convalida o se non esiste alcuna voce per il server di pubblicazione e il database di pubblicazione, *error_number* e *error_severity* restituiscono 0 e *error_message* Restituisce null.  
  
 Se è richiesta la convalida, la convalida stored procedure [sp_validate_redirected_publisher &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md) viene chiamato per verificare che la destinazione del reindirizzamento sia un host adatto per il database di pubblicazione. Se la convalida ha esito positivo, **sp_get_redirected_publisher** restituisce il nome del server di pubblicazione reindirizzato, 0 per il *error_number* e *error_severity* colonne e valori null nella il *error_message* colonna.  
  
 Se la convalida viene richiesta e non riesce, il nome del server di pubblicazione reindirizzato viene restituito insieme alle informazioni sull'errore.  
  
## <a name="permissions"></a>Permissions  
 Chiamante deve essere un membro del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database per il database di distribuzione o un membro di un elenco di accesso per una pubblicazione definita associato al database di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
