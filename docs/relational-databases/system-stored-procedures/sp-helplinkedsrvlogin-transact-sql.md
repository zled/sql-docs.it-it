---
title: sp_helplinkedsrvlogin (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helplinkedsrvlogin_TSQL
- sp_helplinkedsrvlogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplinkedsrvlogin
ms.assetid: a2b1eba0-bf71-47e7-a4c7-9f55feec82a3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 41a7d16799315c62c025087c64cc11339c19af01
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sphelplinkedsrvlogin-transact-sql"></a>sp_helplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui mapping degli account di accesso definiti per un determinato server collegato utilizzato per query distribuite e stored procedure remote.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helplinkedsrvlogin [ [ @rmtsrvname = ] 'rmtsrvname' ]   
     [ , [ @locallogin = ] 'locallogin' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@rmtsrvname=**] **'***rmtsrvname***'**  
 Nome del server collegato a cui viene applicato il mapping dell'account di accesso. *rmtsrvname* è **sysname**, con un valore predefinito è NULL. NULL indica che vengono restituiti i mapping degli account di accesso definiti per tutti i server collegati nel computer locale in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione.  
  
 [  **@locallogin=**] **'***locallogin***'**  
 È il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso nel server locale che dispone di un mapping per il server collegato *rmtsrvname*. *locallogin* è **sysname**, con un valore predefinito è NULL. NULL specifica che tutti i mapping di account di accesso definiti in *rmtsrvname* vengono restituiti. Se non è NULL, un mapping per *locallogin* a *rmtsrvname* deve essere già esistente. *locallogin* può essere un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso o un utente di Windows. È necessario che l'utente di Windows disponga dell'accesso a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ottenuto tramite concessione diretta o in base all'appartenenza a un gruppo di Windows che dispone dell'accesso.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**Server collegato**|**sysname**|Nome del server collegato.|  
|**Account di accesso locale**|**sysname**|Account di accesso locale a cui fa riferimento il mapping.|  
|**Mapping automatico**|**smallint**|0 = **account di accesso locale** viene eseguito il mapping a **account di accesso remoto** durante la connessione a **Server collegato**.<br /><br /> 1 = **account di accesso locale** viene eseguito il mapping allo stesso account di accesso e password quando ci si connette a **Server collegato**.|  
|**Account di accesso remoto**|**sysname**|Nome di account di accesso su **LinkedServer** che viene eseguito il mapping a **LocalLogin** quando **IsSelfMapping** è 0. Se **IsSelfMapping** è 1, **RemoteLogin** è NULL.|  
  
## <a name="remarks"></a>Osservazioni  
 Prima di eliminare i mapping di account di accesso, utilizzare **sp_helplinkedsrvlogin** per determinare i server collegati coinvolti.  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni non vengono controllate.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-displaying-all-login-mappings-for-all-linked-servers"></a>A. Visualizzazione dei mapping degli account di accesso per tutti i server collegati  
 Nell'esempio seguente vengono visualizzati i mapping degli account di accesso per tutti i server collegati definiti nel computer locale in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione.  
  
```  
EXEC sp_helplinkedsrvlogin;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Accounts         NULL          1               NULL  
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
Marketing        NULL          1               NULL  
  
(4 row(s) affected)  
```  
  
### <a name="b-displaying-all-login-mappings-for-a-linked-server"></a>B. Visualizzazione di tutti i mapping degli account di accesso per un server collegato  
 Nell'esempio seguente vengono visualizzati tutti i mapping degli account di accesso definiti a livello locale per il server collegato `Sales`.  
  
```  
EXEC sp_helplinkedsrvlogin 'Sales';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
### <a name="c-displaying-all-login-mappings-for-a-local-login"></a>C. Visualizzazione di tutti i mapping per un account di accesso locale  
 Nell'esempio seguente vengono visualizzati tutti i mapping definiti a livello locale per l'account di accesso `Mary`.  
  
```  
EXEC sp_helplinkedsrvlogin NULL, 'Mary';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Linked Server    Local Login   Is Self Mapping Remote Login   
---------------- ------------- --------------- --------------   
Sales            NULL          1               NULL  
Sales            Mary          0               sa  
  
(2 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [la procedura sp_droplinkedsrvlogin &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
