---
title: sp_validate_redirected_publisher (Transact-SQL) | Documenti Microsoft
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
- sp_validate_redirected_publisher
- sp_validate_redirected_publisher_TSQL
helpviewer_keywords: sp_validate_redirected_publisher
ms.assetid: 2b7fdbad-17e4-4442-b0b2-9b5e8f84b91d
caps.latest.revision: "9"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bafe71c88b5fc47c822275ebfb9be102db65b22b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spvalidateredirectedpublisher-transact-sql"></a>sp_validate_redirected_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Verifica che l'host corrente per il database del server di pubblicazione sia in grado di supportare la replica. Deve essere eseguito da un database di distribuzione. Questa procedura viene chiamata da **sp_get_redirected_publisher**.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
      sp_validate_redirected_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@original_publisher**  =] **'***original_publisher***'**  
 Il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che ha pubblicato in origine il database. *original_publisher* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publisher_db**  =] **'***publisher_db***'**  
 Il nome del database da pubblicare. *publisher_db* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@redirected_publisher**  =] **'***redirected_publisher***'**  
 La destinazione di reindirizzamento specificato al momento **sp_redirect_publisher** è stato chiamato per la coppia server di pubblicazione/database. *redirected_publisher* è **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 nessuna.  
  
## <a name="remarks"></a>Osservazioni  
 Se non esiste alcuna voce per il server di pubblicazione e il database di pubblicazione, **sp_validate_redirected_publisher** restituisce null nel parametro di output  *@redirected_publisher* . Se una voce esiste, viene restituita nel parametro di output sia nei casi di esito positivo che di esito negativo.  
  
 Se la convalida ha esito positivo, **sp_validate_redirected_publisher** restituisce un'indicazione di esito positivo.  
  
 Se la convalida non riesce, vengono generati gli errori con la relativa descrizione.  
  
## <a name="permissions"></a>Permissions  
 Chiamante deve essere un membro del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database per il database di distribuzione o un membro di un elenco di accesso per una pubblicazione definita associato al database di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_get_redirected_publisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_redirect_publisher &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
