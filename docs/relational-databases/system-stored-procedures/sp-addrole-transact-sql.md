---
title: sp_addrole (Transact-SQL) | Documenti Microsoft
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
- sp_addrole
- sp_addrole_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_addrole
ms.assetid: e8a21642-8440-419a-8585-93d3d9d44f00
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 070e1d0e71b49689e547dc29300bf5a5476d17ec
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spaddrole-transact-sql"></a>sp_addrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un nuovo ruolo di database nel database corrente.  
  
> [!IMPORTANT]  
>  **sp_addrole** è inclusa per compatibilità con le versioni precedenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e potrebbe non essere supportato nelle versioni future. Utilizzare [CREATE ROLE](../../t-sql/statements/create-role-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addrole [ @rolename = ] 'role' [ , [ @ownername = ] 'owner' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@rolename =** ] **'***ruolo***'**  
 Nome del nuovo ruolo del database. *ruolo* è un **sysname**, non prevede alcun valore predefinito. *ruolo* deve essere un identificatore (ID) valido e non deve essere già presente nel database corrente.  
  
 [  **@ownername =**] **'***proprietario***'**  
 Proprietario del nuovo ruolo del database. *proprietario* è un **sysname**, con valore predefinito è l'utente corrente. *proprietario* deve essere un utente del database o ruolo del database nel database corrente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 I nomi dei ruoli di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possono includere da 1 a 128 caratteri. Sono consentiti simboli, numeri e lettere. I nomi dei ruoli predefiniti del database non è possibile: contiene un carattere barra rovesciata (\\), essere NULL o una stringa vuota (**'**).  
  
 Dopo aver aggiunto un ruolo del database, utilizzare [sp_addrolemember &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md) per aggiungere entità al ruolo. Quando si utilizza l'istruzione GRANT, DENY o REVOKE per applicare autorizzazioni al ruolo, i membri corrispondenti ereditano tali autorizzazioni come se fossero state assegnate direttamente ai relativi account.  
  
> [!NOTE]  
>  Non è possibile creare nuovi ruoli di server. I ruoli possono essere creati solo a livello di database.  
  
 **sp_addrole** non può essere utilizzato all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CREATE ROLE per il database. Per la creazione di uno schema, è richiesta l'autorizzazione CREATE SCHEMA per il database. Se *proprietario* è specificato come un utente o gruppo, richiede IMPERSONATE su tale utente o gruppo. Se *proprietario* è specificato come un ruolo, è necessaria l'autorizzazione ALTER per tale ruolo o di un membro del ruolo. Se owner è specificato come ruolo di applicazione, è richiesta l'autorizzazione ALTER per quel ruolo di applicazione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene aggiunto un nuovo ruolo `Managers` al database corrente.  
  
```  
EXEC sp_addrole 'Managers';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)  
  
  
