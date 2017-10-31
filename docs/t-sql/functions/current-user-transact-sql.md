---
title: CURRENT_USER (Transact-SQL) | Documenti Microsoft
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
- CURRENT_USER
- CURRENT_USER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- current user names
- niladic functions
- CURRENT_USER
- users [SQL Server], names
ms.assetid: 29248949-325b-4063-9f55-5a445fb35c6e
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: 7fbb100c34c2a8b1b33a585cb5ead6aaca56f0d8
ms.contentlocale: it-it
ms.lasthandoff: 10/17/2017

---
# <a name="currentuser-transact-sql"></a>CURRENT_USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce il nome dell'utente corrente. Questa funzione equivale a USER_NAME().
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CURRENT_USER  
```  

## <a name="return-types"></a>Tipi restituiti
**sysname**
  
## <a name="remarks"></a>Osservazioni  
CURRENT_USER restituisce il nome del contesto di sicurezza corrente. Se si esegue CURRENT_USER dopo una chiamata EXECUTE AS per cambiare contesto, CURRENT_USER restituirà il nome del contesto rappresentato. Se un'entità di Windows ha eseguito l'accesso al database tramite l'appartenenza a un gruppo, verrà restituito il nome dell'entità di Windows anziché il nome del gruppo.
  
Per restituire l'account di accesso dell'utente corrente, vedere [SUSER_NAME &#40; Transact-SQL &#41; ](../../t-sql/functions/suser-name-transact-sql.md) e [SYSTEM_USER &#40; Transact-SQL &#41; ](../../t-sql/functions/system-user-transact-sql.md).
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-currentuser-to-return-the-current-user-name"></a>A. Utilizzo di CURRENT_USER per restituire il nome dell'utente corrente  
Nell'esempio seguente viene restituito il nome dell'utente corrente.
  
```sql
SELECT CURRENT_USER;  
GO  
```  
  
### <a name="b-using-currentuser-as-a-default-constraint"></a>B. Utilizzo di CURRENT_USER come vincolo DEFAULT  
Nell'esempio seguente viene creata una tabella che utilizza `CURRENT_USER` come vincolo `DEFAULT` per la colonna `order_person` di una riga di dati sulle vendite.
  
```sql
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES  
      WHERE TABLE_NAME = 'orders22')  
   DROP TABLE orders22;  
GO  
SET NOCOUNT ON;  
CREATE TABLE orders22  
(  
order_id int IDENTITY(1000, 1) NOT NULL,
cust_id  int NOT NULL,
order_date smalldatetime NOT NULL DEFAULT GETDATE(),
order_amt money NOT NULL,
order_person char(30) NOT NULL DEFAULT CURRENT_USER
);  
GO  
```  
  
Nel codice seguente viene inserito un record nella tabella. Il nome dell'utente che esegue queste istruzione è `Wanida`.
  
```sql
INSERT orders22 (cust_id, order_amt)  
VALUES (5105, 577.95);  
GO  
SET NOCOUNT OFF;  
GO  
```  
  
La query seguente consente di selezionare tutte le informazioni della tabella `orders22`.
  
```sql
SELECT * FROM orders22;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
order_id    cust_id     order_date           order_amt    order_person
----------- ----------- -------------------- ------------ ------------
1000        5105        2005-04-03 23:34:00  577.95       Wanida
  
(1 row(s) affected)
```
  
### <a name="c-using-currentuser-from-an-impersonated-context"></a>C. Utilizzo di CURRENT_USER da un contesto rappresentato  
Nell'esempio seguente l'utente `Wanida` esegue il codice [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente.
  
```sql
SELECT CURRENT_USER;  
GO  
EXECUTE AS USER = 'Arnalfo';  
GO  
SELECT CURRENT_USER;  
GO  
REVERT;  
GO  
SELECT CURRENT_USER;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Wanida
Arnalfo
Wanida
```
  
## <a name="see-also"></a>Vedere anche
[USER_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/user-name-transact-sql.md)  
[SYSTEM_USER &#40; Transact-SQL &#41;](../../t-sql/functions/system-user-transact-sql.md)  
[sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)  
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Funzioni di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)
  
  


