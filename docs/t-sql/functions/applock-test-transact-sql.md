---
title: APPLOCK_TEST (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- APPLOCK_TEST_TSQL
- APPLOCK_TEST
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], applications
- APPLOCK_TEST function
- applications [SQL Server], locks
- sessions [SQL Server], application locks
- testing application locks
ms.assetid: 4ea33d04-f8e9-46ff-ae61-985bd3eaca2c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f4009a151873bf989a39bc4fb91ec3a9963af9f2
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="applocktest-transact-sql"></a>APPLOCK_TEST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce le informazioni relative alla possibilità o meno di concedere un blocco per una risorsa dell'applicazione specifica a un proprietario di blocchi specifico senza acquisire il blocco stesso. APPLOCK_TEST è una funzione di blocco a livello di applicazione e viene eseguita nel database corrente. L'ambito dei blocchi a livello di applicazione è il database.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
APPLOCK_TEST ( 'database_principal' , 'resource_name' , 'lock_mode' , 'lock_owner' )  
```  
  
## <a name="arguments"></a>Argomenti  
**'** *database_principal* **'**  
Utente, ruolo o ruolo applicazione a cui è possibile concedere autorizzazioni per gli oggetti nel database. Il chiamante della funzione deve essere un membro di *database_principal*, **dbo**, o **db_owner** ruolo predefinito del database per chiamare la funzione correttamente.
  
**'** *resource_name* **'**  
Nome di una risorsa di blocco specificato nell'applicazione client. L'applicazione deve garantire che la risorsa sia univoca. Il nome specificato viene sottoposto internamente ad hashing per creare un valore che è possibile archiviare in Gestione blocchi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name*è **nvarchar (255)** prevede alcun valore predefinito. *resource_name* viene eseguito un confronto binario e tra maiuscole e minuscole, indipendentemente dalle impostazioni delle regole di confronto del database corrente.
  
**'** *lock_mode* **'**  
Modalità di blocco da acquisire per una particolare risorsa. *lock_mode* è **nvarchar(32)** e nessun valore predefinito. Il valore può essere uno dei seguenti: **Shared**, **aggiornamento**, **IntentShared**, **IntentExclusive**, **esclusivo** .
  
**'** *lock_owner* **'**  
È il proprietario del blocco, ovvero il *lock_owner* valore quando è stato richiesto il blocco. *lock_owner* è **nvarchar(32)**. Il valore può essere **transazione** (impostazione predefinita) o **sessione**. Se predefinito o **transazione** è specificato in modo esplicito, necessario eseguire APPLOCK_TEST dall'interno di una transazione.
  
## <a name="return-types"></a>Tipi restituiti
**smallint**
  
## <a name="return-value"></a>Valore restituito
Restituisce 0 se il blocco non può essere concesso al proprietario specificato. In caso contrario restituisce 1.
  
## <a name="function-properties"></a>Proprietà (funzione)
**Non deterministiche**
  
**Nonindexable**
  
**Nonparallelizable**
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente, due utenti (**utente** e **utente B**) con sessioni separate eseguono la seguente sequenza di [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzioni.
  
**L'utente** esegue:
  
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
  
**L'utente B** quindi esegue:
  
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
  
**L'utente** quindi esegue:
  
```sql
EXEC sp_releaseapplock @Resource='Form1', @DbPrincipal='public';  
GO  
```  
  
**L'utente B** quindi esegue:
  
```sql
SELECT APPLOCK_TEST('public', 'Form1', 'Exclusive', 'Transaction');  
--Result set: '1' (The lock is grantable.)  
GO  
```  
  
**L'utente** e **utente B** quindi eseguono entrambi:
  
```sql
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[APPLOCK_MODE &#40; Transact-SQL &#41;](../../t-sql/functions/applock-mode-transact-sql.md)  
[sp_getapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
[sp_releaseapplock &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)
  
  
