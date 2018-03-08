---
title: IS_MEMBER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_MEMBER
- IS_MEMBER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], members
- current member status
- roles [SQL Server], members
- testing member status
- members [SQL Server]
- checking member status
- IS_MEMBER function
- verifying member status
- groups [SQL Server], members
- members [SQL Server], verifying
ms.assetid: 77cb68a0-19b7-4fe1-ab17-e5587699631b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e14fc4cf70066c21a8a837760d4325a19ae4ff1c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="ismember-transact-sql"></a>IS_MEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Indica se l'utente corrente è membro del gruppo di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows o del ruolo di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IS_MEMBER ( { 'group' | 'role' } )  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *gruppo* **'**  
**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 È il nome del gruppo di Windows che viene controllato; deve essere nel formato *dominio*\\*gruppo*. *gruppo* è **sysname**.  
  
 **'** *ruolo* **'**  
 È il nome del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruolo che viene eseguita la verifica. *ruolo* è **sysname** e possono includere i predefiniti o definiti dall'utente, ma non i ruoli server del database.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 IS_MEMBER restituisce i valori seguenti.  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0|Utente corrente non è un membro di *gruppo* o *ruolo*.|  
|1|Utente corrente è un membro di *gruppo* o *ruolo*.|  
|NULL|Entrambi *gruppo* o *ruolo* non è valido. Quando la query viene eseguita da un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o da un account di accesso che utilizza un ruolo applicazione esegue una query, restituisce NULL per un gruppo di Windows.|  
  
 IS_MEMBER determina l'appartenenza al gruppo di Windows tramite l'analisi di un token di accesso creato da Windows. Il token di accesso non riflette le modifiche a livello di appartenenza al gruppo apportate dopo la connessione da parte di un utente a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o un ruolo applicazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non possono eseguire una query sull'appartenenza del gruppo di Windows.  
  
 Per aggiungere e rimuovere membri da un ruolo del database, utilizzare [ALTER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-role-transact-sql.md). Per aggiungere e rimuovere membri da un ruolo del server, utilizzare [ALTER SERVER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 Questa funzione valuta l'appartenenza al ruolo, non l'autorizzazione sottostante. Ad esempio, il **db_owner** ruolo predefinito del database è il **CONTROL DATABASE** autorizzazione. Se l'utente dispone di **CONTROL DATABASE** autorizzazione ma non è un membro del ruolo, questa funzione indicherà correttamente che l'utente non è un membro del **db_owner** ruolo, anche se l'utente ha lo stesso autorizzazioni.  
  
 I membri del **sysadmin** ruolo predefinito del server immettere tutti i database come il **dbo** utente. Verifica dell'autorizzazione per il membro del **sysadmin** ruolo predefinito del server, controlla le autorizzazioni per **dbo**, non l'account di accesso originale. Poiché **dbo** non può essere aggiunto a un ruolo del database e non esiste in gruppi di Windows, **dbo** restituirà sempre 0 (o NULL se il ruolo non esiste).  
  
## <a name="related-functions"></a>Funzioni correlate  
 Per determinare se un altro [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso è un membro di un ruolo del database, utilizzare [IS_ROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-rolemember-transact-sql.md). Per determinare se un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso è un membro di un ruolo del server, utilizzare [IS_SRVROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-srvrolemember-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene verificato se l'utente corrente è membro di un ruolo di database oppure di un gruppo di domini di Windows.  
  
```  
-- Test membership in db_owner and print appropriate message.  
IF IS_MEMBER ('db_owner') = 1  
   PRINT 'Current user is a member of the db_owner role'  
ELSE IF IS_MEMBER ('db_owner') = 0  
   PRINT 'Current user is NOT a member of the db_owner role'  
ELSE IF IS_MEMBER ('db_owner') IS NULL  
   PRINT 'ERROR: Invalid group / role specified';  
GO  
  
-- Execute SELECT if user is a member of ADVWORKS\Shipping.  
IF IS_MEMBER ('ADVWORKS\Shipping') = 1  
   SELECT 'User ' + USER + ' is a member of ADVWORKS\Shipping.';   
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IS_SRVROLEMEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-srvrolemember-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
