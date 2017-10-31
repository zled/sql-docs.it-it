---
title: IS_SRVROLEMEMBER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_SRVROLEMEMBER_TSQL
- IS_SRVROLEMEMBER
dev_langs:
- TSQL
helpviewer_keywords:
- roles [SQL Server], members
- IS_SRVROLEMEMBER function
- members [SQL Server], verifying
ms.assetid: 3241a44a-6958-415b-b8b7-2a1207c36ab3
caps.latest.revision: 65
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c26c0c1f4cb6a22f50cdc6a87d7a31f25b65e138
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="issrvrolemember-transact-sql"></a>IS_SRVROLEMEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Indica se un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è un membro del ruolo del server specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IS_SRVROLEMEMBER ( 'role' [ , 'login' ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *ruolo* **'**  
 Nome del ruolo del server sottoposto al controllo. *ruolo* è **sysname**.  
  
 I valori validi per *ruolo* sono ruoli del server definito dall'utente e le operazioni seguenti ruoli predefiniti del server:  
  
|||  
|-|-|  
|sysadmin|serveradmin|  
|dbcreator|setupadmin|  
|bulkadmin|securityadmin|  
|diskadmin|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> pubblico|  
|processadmin||  
  
 **'** *accesso* **'**  
 È il nome del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso da verificare. *account di accesso* è **sysname**, con un valore predefinito è NULL. Se non si specifica alcun valore, il risultato sarà basato sul contesto di esecuzione corrente. Se nel parametro è inclusa la parola NULL, verrà restituito NULL.  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0|*account di accesso* non è un membro di *ruolo*.<br /><br /> In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], questa istruzione restituisce sempre 0.|  
|1|*account di accesso* è un membro di *ruolo*.|  
|NULL|*ruolo* o *accesso* non è valido o non si dispone delle autorizzazioni necessarie per visualizzare l'appartenenza al ruolo.|  
  
## <a name="remarks"></a>Osservazioni  
 UseIS_SRVROLEMEMBER per determinare se l'utente corrente può eseguire un'azione che richiede le autorizzazioni del ruolo del server.  
  
 Se un account di accesso di Windows, ad esempio Contoso\Mary5, viene specificato per *accesso*, **IS_SRVROLEMEMBER** restituisce **NULL**, a meno che l'account di accesso sia stato concesso o negato l'accesso diretto al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se l'opzione facoltativa *accesso* parametro non viene fornito e se *accesso* è un account di dominio di Windows, potrebbe essere un membro di un ruolo predefinito del server tramite l'appartenenza a un gruppo di Windows. Per risolvere tali problemi di appartenenza indiretta, IS_SRVROLEMEMBER richiede le informazioni di appartenenza ai gruppi di Windows al controller di dominio. Se il controller di dominio non è accessibile o non risponde, **IS_SRVROLEMEMBER** restituisce le informazioni di appartenenza al ruolo accounting per l'utente e solo i gruppi locali. Se l'utente specificato non è l'utente corrente, il valore restituito da IS_SRVROLEMEMBER potrebbe essere diverso dall'ultimo aggiornamento dei dati dell'autenticatore, ad esempio Active Directory, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se il parametro per l'account di accesso facoltativo viene fornito, l'account di accesso di Windows su cui vengono eseguite query deve essere presente in sys.server_principals. In caso contrario, IS_SRVROLEMEMBER restituisce NULL. Questo valore indica che l'account di accesso non è valido.  
  
 Quando il parametro di accesso è un account di accesso di dominio o è basato su un gruppo di Windows e il controller di dominio non è accessibile, le chiamate a IS_SRVROLEMEMBER hanno esito negativo e possono restituire dati errati o incompleti.  
  
 Se il controller di dominio non è disponibile, la chiamata a IS_SRVROLEMEMBER restituisce informazioni accurate quando l'entità di Windows può essere autenticata localmente, ad esempio come account Windows locale o come account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **IS_SRVROLEMEMBER** restituisce sempre 0 quando viene utilizzato un gruppo di Windows come argomento di accesso e tale gruppo è un membro di un altro gruppo di Windows che, a sua volta, un membro del ruolo del server specificato.  
  
 L'impostazione di controllo Account utente (UAC) potrebbe causare i restituiscono risultati diversi. Questo dipende dal fatto che l'utente acceda al server come membro di un gruppo di Windows o come utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specifico.  
  
 Questa funzione valuta l'appartenenza al ruolo, non l'autorizzazione sottostante. Ad esempio, il **sysadmin** ruolo predefinito del server di **CONTROL SERVER** autorizzazione. Se l'utente dispone di **CONTROL SERVER** autorizzazione ma non è un membro del ruolo, questa funzione indicherà correttamente che l'utente non è un membro del **sysadmin** ruolo, anche se l'utente ha lo stesso autorizzazioni.  
  
## <a name="related-functions"></a>Funzioni correlate  
 Per determinare se l'utente corrente è un membro del gruppo di Windows specificato o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruolo del database, utilizzare [IS_MEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-member-transact-sql.md). Per determinare se un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso è un membro di un ruolo del database, utilizzare [IS_ROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-rolemember-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW DEFINITION per il ruolo del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene indicato se l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'utente corrente è un membro del ruolo predefinito del server `sysadmin`.  
  
```  
IF IS_SRVROLEMEMBER ('sysadmin') = 1  
   print 'Current user''s login is a member of the sysadmin role'  
ELSE IF IS_SRVROLEMEMBER ('sysadmin') = 0  
   print 'Current user''s login is NOT a member of the sysadmin role'  
ELSE IF IS_SRVROLEMEMBER ('sysadmin') IS NULL  
   print 'ERROR: The server role specified is not valid.';  
```  
  
 Nell'esempio seguente indica se l'account di dominio Pat è un membro del **diskadmin** ruolo predefinito del server.  
  
```  
SELECT IS_SRVROLEMEMBER('diskadmin', 'Contoso\Pat');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IS_MEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-member-transact-sql.md)   
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  

