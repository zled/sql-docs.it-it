---
title: sp_changeobjectowner (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sp_changeobjectowner_TSQL
- sp_changeobjectowner
dev_langs: TSQL
helpviewer_keywords: sp_changeobjectowner
ms.assetid: 45b3dc1c-1cde-45b7-a248-5195c12973e9
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 00d4fbb90a767294e3d529e6fa5706eecfd841f1
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spchangeobjectowner-transact-sql"></a>sp_changeobjectowner (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica il proprietario di un oggetto del database corrente.  
  
> [!IMPORTANT]  
>  Questa stored procedure funziona solo con gli oggetti disponibili in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [ALTER SCHEMA](../../t-sql/statements/alter-schema-transact-sql.md) o [ALTER AUTHORIZATION](../../t-sql/statements/alter-authorization-transact-sql.md) invece. **sp_changeobjectowner** modifica sia lo schema sia il proprietario. Per mantenere la compatibilità con le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], questa stored procedure modifica i proprietari degli oggetti solo quando sia il proprietario corrente che il nuovo proprietario possiedono schemi il cui nome corrisponde al relativo nome utente di database.  
  
> [!IMPORTANT]  
>  A questa stored procedure è stato aggiunto un nuovo requisito di autorizzazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_changeobjectowner [ @objname = ] 'object' , [ @newowner = ] 'owner'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@objname =** ] **'***oggetto***'**  
 Nome di una tabella, vista, funzione definita dall'utente o stored procedure esistente nel database corrente. *oggetto* è un **nvarchar(776)**, non prevede alcun valore predefinito. *oggetto* può essere qualificato con il proprietario dell'oggetto esistente, nel formato *existing_owner***.** *oggetto* se lo schema e il relativo proprietario hanno lo stesso nome.  
  
 [  **@newowner=**] **'***proprietario* **'**  
 Nome dell'account di sicurezza che rappresenta il nuovo proprietario dell'oggetto. *proprietario* è **sysname**, non prevede alcun valore predefinito. *proprietario* deve essere un utente valido del database, ruolo del server [!INCLUDE[msCoName](../../includes/msconame-md.md)] account di accesso di Windows o il gruppo di Windows con accesso al database corrente. Se il nuovo proprietario è un utente di Windows o un gruppo di Windows per cui non esiste un'entità corrispondente a livello di database, verrà creato un utente di database.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_changeobjectowner** rimuove tutte le autorizzazioni esistenti dall'oggetto. È necessario riapplicare le autorizzazioni che si desidera mantenere dopo l'esecuzione **sp_changeobjectowner**. È pertanto consigliabile includere le autorizzazioni esistenti prima dell'esecuzione **sp_changeobjectowner**. Dopo avere modificato il proprietario dell'oggetto, è possibile eseguire lo script per riapplicare le autorizzazioni. È prima necessario modificare il proprietario dell'oggetto nello script.  
  
 Per modificare il proprietario di un'entità a sicurezza diretta, utilizzare ALTER AUTHORIZATION. Per modificare uno schema, utilizzare ALTER SCHEMA.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'appartenenza di **db_owner** fissa, o l'appartenenza al ruolo del database sia nel **db_ddladmin** ruolo predefinito del database e **db_securityadmin** ruolo predefinito del database, e anche dell'autorizzazione CONTROL per l'oggetto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene modificato il proprietario della tabella `authors` in `Corporate\GeorgeW`.  
  
```  
EXEC sp_changeobjectowner 'authors', 'Corporate\GeorgeW';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [L'autorizzazione ALTER SCHEMA &#40; Transact-SQL &#41;](../../t-sql/statements/alter-schema-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [AUTORIZZAZIONE ALTER &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_changedbowner &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
