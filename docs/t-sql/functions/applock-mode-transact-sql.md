---
title: APPLOCK_MODE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- APPLOCK_MODE_TSQL
- APPLOCK_MODE
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], applications
- applications [SQL Server], locks
- sessions [SQL Server], application locks
- APPLOCK_MODE function
ms.assetid: e43d4917-77f1-45cc-b231-68ba7fee3385
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ceec0a5465187e1b470bd9eb8b1039a5b3d60aae
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="applockmode-transact-sql"></a>APPLOCK_MODE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce la modalità di blocco acquisita dal proprietario del blocco per una particolare risorsa di applicazione. APPLOCK_MODE è una funzione di blocco a livello di applicazione e viene eseguita sul database corrente. L'ambito dei blocchi a livello di applicazione è il database.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
APPLOCK_MODE( 'database_principal' , 'resource_name' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>Argomenti  
'*database_principal*'  
Utente, ruolo o ruolo applicazione a cui è possibile concedere autorizzazioni per gli oggetti nel database. Il chiamante della funzione deve essere un membro di *database_principal*, dbo o db_owner ruolo predefinito del database per chiamare la funzione correttamente.
  
'*resource_name*'  
Nome di una risorsa di blocco specificato nell'applicazione client. L'applicazione deve garantire che il nome della risorsa sia univoco. Il nome specificato viene sottoposto internamente ad hashing per creare un valore che è possibile archiviare in Gestione blocchi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name*è **nvarchar (255)** prevede alcun valore predefinito. *resource_name* è di tipo binary confrontati e tra maiuscole e minuscole indipendentemente dalle impostazioni delle regole di confronto del database corrente.
  
'*lock_owner*'  
È il proprietario del blocco, ovvero il *lock_owner* valore quando è stato richiesto il blocco. *lock_owner* è **nvarchar(32)**, e il valore può essere **transazione** (impostazione predefinita) o **sessione**.
  
## <a name="return-types"></a>Tipi restituiti
**nvarchar(32)**
  
## <a name="return-value"></a>Valore restituito
Restituisce la modalità di blocco acquisita dal proprietario del blocco per una particolare risorsa di applicazione. I possibili valori della modalità di blocco sono i seguenti:
  
||||  
|-|-|-|  
|**NoLock**|**Update**|**\*SharedIntentExclusive**|  
|**IntentShared**|**IntentExclusive**|**\*UpdateIntentExclusive**|  
|**Condiviso**|**Exclusive**||  
  
*Questa modalità di blocco risulta dalla combinazione di altre modalità di blocco e non può essere acquisita in modo esplicito tramite sp_getapplock.
  
## <a name="function-properties"></a>Proprietà (funzione)
**Non deterministiche**
  
**Nonindexable**
  
**Nonparallelizable**
  
## <a name="examples"></a>Esempi  
Si supponga che due utenti, l'utente A e l'utente B, eseguano la sequenza di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] riportata di seguito in sessioni separate.
  
L'utente A esegue:
  
```sql
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result=sp_getapplock  
    @DbPrincipal='public',  
    @Resource='Form1',  
    @LockMode='Shared',  
    @LockOwner='Transaction';  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
GO  
```  
  
L'utente B quindi esegue:
  
```sql
Use AdventureWorks2012;  
GO  
BEGIN TRAN;  
SELECT APPLOCK_MODE('public', 'Form1', 'Transaction');  
--Result set: NoLock  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Shared', 'Transaction');  
--Result set: 1 (Lock is grantable.)  
  
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: 0 (Lock is not grantable.)  
GO  
```  
  
L'utente A quindi esegue:
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
L'utente B quindi esegue:
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
Gli utenti A e B eseguono quindi l'istruzione seguente:
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[APPLOCK_TEST &#40; Transact-SQL &#41;](../../t-sql/functions/applock-test-transact-sql.md)  
[sp_getapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  

