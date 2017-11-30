---
title: sp_helplogins (Transact-SQL) | Documenti Microsoft
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
- sp_helplogins_TSQL
- sp_helplogins
dev_langs: TSQL
helpviewer_keywords: sp_helplogins
ms.assetid: f9ad3767-5b9f-420d-8922-b637811404f7
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75e0521889f38db02bfdc9eabd3332d3fa76afb9
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sphelplogins-transact-sql"></a>sp_helplogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sugli account di accesso e sugli utenti corrispondenti in ogni database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helplogins [ [ @LoginNamePattern = ] 'login' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@LoginNamePattern =** ] **'***accesso***'**  
 Nome dell'account di accesso. *account di accesso* è **sysname**, con un valore predefinito è NULL. *account di accesso* deve esistere se specificato. Se *accesso* viene omesso, vengono restituite informazioni su tutti gli account di accesso.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Il primo report contiene le informazioni su ogni account di accesso specificato, come illustrato nella tabella seguente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Nome dell'account di accesso.|  
|**SID**|**varbinary (85)**|ID di sicurezza (SID) dell'account di accesso.|  
|**DefDBName**|**sysname**|Database predefinito che **LoginName** utilizza per la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**DefLangName**|**sysname**|Lingua predefinita utilizzata da **LoginName**.|  
|**Auser**|**Char (5)**|Yes = **LoginName** ha un nome utente associato in un database.<br /><br /> No = **LoginName** non dispone di un nome utente associato.|  
|**Associata**|**Char(7)**|Yes = **LoginName** ha un account di accesso remoto associato.<br /><br /> No = **LoginName** non dispone di un account di accesso associato.|  
  
 Il secondo report contiene informazioni sugli utenti sui quali viene eseguito il mapping a ogni account di accesso e le appartenenze al ruolo dell'account di acceso, come illustrato nella tabella seguente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Nome dell'account di accesso.|  
|**DBName**|**sysname**|Database predefinito che **LoginName** utilizza per la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**UserName**|**sysname**|Account utente che **LoginName** viene eseguito il mapping nella **DBName**e i ruoli che **LoginName** è un membro nel **DBName**.|  
|**UserOrAlias**|**Char(8)**|MemberOf = **UserName** è un ruolo.<br /><br /> Utente = **UserName** è un account utente.|  
  
## <a name="remarks"></a>Osservazioni  
 Prima di rimuovere un account di accesso, utilizzare **sp_helplogins** per identificare gli account utente che vengono eseguito il mapping all'account di accesso.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza di **securityadmin** ruolo predefinito del server.  
  
 Per identificare tutti gli account utente mappati a un determinato account di accesso, **sp_helplogins** deve controllare tutti i database all'interno del server. Pertanto, per ogni database nel server, è necessario che sia soddisfatta almeno una delle seguenti condizioni:  
  
-   L'utente che esegue **sp_helplogins** dispone dell'autorizzazione per accedere al database.  
  
-   Il **guest** account utente è abilitato nel database.  
  
 Se **sp_helplogins** non è possibile accedere a un database, **sp_helplogins** restituirà quante più informazioni possibili e visualizzerà il messaggio di errore 15622.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sull'account di accesso `John`.  
  
```  
EXEC sp_helplogins 'John';  
GO  
  
LoginName SID                        DefDBName DefLangName AUser ARemote   
--------- -------------------------- --------- ----------- ----- -------   
John      0x23B348613497D11190C100C  master    us_english  yes   no  
  
(1 row(s) affected)  
  
LoginName   DBName   UserName   UserOrAlias   
---------   ------   --------   -----------   
John        pubs     John       User          
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_helpdb &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpuser &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
