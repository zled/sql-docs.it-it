---
title: IS_ROLEMEMBER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_ROLEMEMBER
- IS_ROLEMEMBER_TSQL
dev_langs: TSQL
helpviewer_keywords:
- roles [SQL Server], members
- IS_ROLEMEMBER function
- members [SQL Server], verifying
ms.assetid: 73efa688-ae91-4014-98bc-1cabe47321f7
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fd8574c27bea00127096dc1f0040c8c3f93e96cb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="isrolemember-transact-sql"></a>IS_ROLEMEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Indica se un'entità di database specificata è un membro del ruolo del database specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IS_ROLEMEMBER ( 'role' [ , 'database_principal' ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *ruolo* **'**  
 Nome del ruolo del database sottoposto al controllo. *ruolo* è **sysname**.  
  
 **'** *database_principal* **'**  
 Nome dell'utente o ruolo del database o del ruolo applicazione da controllare. *database_principal* è **sysname**, con un valore predefinito è NULL. Se non si specifica alcun valore, il risultato sarà basato sul contesto di esecuzione corrente. Se nel parametro è inclusa la parola NULL, verrà restituito NULL.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0|*database_principal* non è un membro di *ruolo*.|  
|1|*database_principal* è un membro di *ruolo*.|  
|NULL|*database_principal* o *ruolo* non è valido o non si dispone delle autorizzazioni necessarie per visualizzare l'appartenenza al ruolo.|  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare IS_ROLEMEMBER per determinare se l'utente corrente è in grado di eseguire un'azione che richiede le autorizzazioni del ruolo del database.  
  
 Se *database_principal* è basata su un account di accesso di Windows, ad esempio Contoso\Mary5, IS_ROLEMEMBER restituisce NULL, a meno che il *database_principal* sia stato concesso o negato l'accesso diretto a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se l'opzione facoltativa *database_principal* parametro non viene fornito e se il *database_principal* si basa su un account di dominio di Windows, potrebbe essere un membro di un ruolo del database tramite l'appartenenza a un gruppo di Windows . Per risolvere tali problemi di appartenenza indiretta, IS_ROLEMEMBER richiede le informazioni di appartenenza ai gruppi di Windows al controller di dominio. Se il controller di dominio non è accessibile o non risponde, IS_ROLEMEMBER restituisce le informazioni di appartenenza ai ruoli prendendo in considerazione solo l'utente e i gruppi locali. Se l'utente specificato non è l'utente corrente, il valore restituito da IS_ROLEMEMBER potrebbe essere diverso dall'ultimo aggiornamento dei dati dell'autenticatore, ad esempio Active Directory, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se l'opzione facoltativa *database_principal* parametro viene specificato, l'entità di database che viene eseguita la query deve essere presente in sys. database_principals o IS_ROLEMEMBER restituisce NULL. Ciò indica che il *database_principal* non è valido in questo database.  
  
 Quando il *database_principal* parametro si basa su un account di accesso di dominio o in base a un gruppo di Windows e il controller di dominio non è accessibile, le chiamate a IS_ROLEMEMBER avrà esito negativo e possono restituire dati errati o incompleti.  
  
 Se il controller di dominio non è disponibile, la chiamata a IS_ROLEMEMBER restituisce informazioni accurate quando l'entità di Windows può essere autenticata localmente, ad esempio come account Windows locale o come account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **IS_ROLEMEMBER** restituisce sempre 0 quando viene utilizzato un gruppo di Windows come argomento dell'entità di database e tale gruppo è un membro di un altro gruppo di Windows che, a sua volta, un membro del ruolo del database specificato.  
  
 Il controllo Account utente (UAC) trovato [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] e Windows Server 2008 potrebbe restituire anche risultati diversi. Questo dipende dal fatto che l'utente acceda al server come membro di un gruppo di Windows o come utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specifico.  
  
 Questa funzione valuta l'appartenenza al ruolo, non l'autorizzazione sottostante. Ad esempio, il **db_owner** ruolo predefinito del database è il **CONTROL DATABASE** autorizzazione. Se l'utente dispone di **CONTROL DATABASE** autorizzazione ma non è un membro del ruolo, questa funzione indicherà correttamente che l'utente non è un membro del **db_owner** ruolo, anche se l'utente ha lo stesso autorizzazioni.  
  
## <a name="related-functions"></a>Funzioni correlate  
 Per determinare se l'utente corrente è un membro del gruppo di Windows specificato o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruolo del database, utilizzare [IS_MEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-member-transact-sql.md). Per determinare se un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso è un membro di un ruolo del server, utilizzare [IS_SRVROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-srvrolemember-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW DEFINITION per il ruolo del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene indicato se l'utente corrente è un membro del ruolo predefinito del database `db_datareader`.  
  
```  
IF IS_ROLEMEMBER ('db_datareader') = 1  
   print 'Current user is a member of the db_datareader role'  
ELSE IF IS_ROLEMEMBER ('db_datareader') = 0  
   print 'Current user is NOT a member of the db_datareader role'  
ELSE IF IS_ROLEMEMBER ('db_datareader') IS NULL  
   print 'ERROR: The database role specified is not valid.';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREAZIONE di ruolo &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [ALTER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [DROP ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [CREATE SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
 [ALTER SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-role-transact-sql.md)   
 [DROP SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [IS_MEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-member-transact-sql.md)   
 [IS_SRVROLEMEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-srvrolemember-transact-sql.md)   
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
