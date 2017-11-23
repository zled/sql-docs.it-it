---
title: sp_bindefault (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 11/25/2015
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_bindefault
- sp_bindefault_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_bindefault
ms.assetid: 3da70c10-68d0-4c16-94a5-9e84c4a520f6
caps.latest.revision: "42"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3e23435d6c0a2db3809722856b9daa6b2d66505
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spbindefault-transact-sql"></a>sp_bindefault (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Associa un valore predefinito a una colonna o a un tipo di dati alias.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]È consigliabile creare definizioni predefinite tramite la parola chiave DEFAULT del [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) o [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) istruzioni invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_bindefault [ @defname = ] 'default' ,   
    [ @objname = ] 'object_name'   
    [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@defname=** ] **'***predefinito***'**  
 Nome del valore predefinito creato tramite CREATE DEFAULT. *predefinito* è **nvarchar(776)**, non prevede alcun valore predefinito.  
  
 [  **@objname=** ] **'***object_name***'**  
 Nome della tabella e della colonna o del tipo di dati alias a cui associare il valore predefinito. *object_name* è **nvarchar(776)** prevede alcun valore predefinito. *object_name* non possono essere definiti con la **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **xml**, o CLR tipi definiti dall'utente.  
  
 Se *object_name* è un nome di una sola parte, viene risolto come tipo di dati alias. Se è un nome in due o tre parti, viene prima risolto come tabella e colonna. Se la risoluzione non riesce, viene risolto come tipo di dati alias. Per impostazione predefinita, le colonne esistenti del tipo di dati alias ereditano *predefinito*, a meno che un valore predefinito è stato associato direttamente alla colonna. Valore predefinito non può essere associato a un **testo**, **ntext**, **immagine**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **xml**, **timestamp**, o CLR colonna di tipo definito dall'utente, una colonna con la proprietà IDENTITY, una colonna calcolata o una colonna che esiste già un vincolo predefinito.  
  
> [!NOTE]  
>  *object_name* può contenere parentesi quadre **[]** come identificatori delimitati. Per altre informazioni, vedere [Identificatori del database](../../relational-databases/databases/database-identifiers.md).  
  
 [  **@futureonly=** ] **'***futureonly_flag***'**  
 Utilizzato solo quando si associa un valore predefinito a un tipo di dati alias. *futureonly_flag* è **varchar(15)** con un valore predefinito è NULL. Quando questo parametro è impostato su **futureonly**, le colonne esistenti di tale tipo di dati non possono ereditare il nuovo valore predefinito. Questo parametro non viene mai utilizzato per l'associazione di un valore predefinito a una colonna. Se *futureonly_flag* è NULL, il nuovo valore predefinito è associato a tutte le colonne del tipo di dati alias alcun valore predefinito o che utilizzano il valore predefinito esistente del tipo di dati alias.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare **sp_bindefault** per associare un nuovo valore predefinito a una colonna, sebbene sia preferibile utilizzare il vincolo predefinito, o a un tipo di dati alias senza disassociare un valore predefinito esistente. Il valore predefinito esistente viene ignorato. Non è possibile associare un valore predefinito a un tipo di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o a un tipo CLR definito dall'utente. Se il valore predefinito non è compatibile con la colonna a cui è stato associato, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] restituisce un messaggio di errore quando si tenta di inserire il valore predefinito, non in fase di associazione.  
  
 Le colonne esistenti del tipo di dati alias ereditano il nuovo valore predefinito, a meno che non è associato un valore predefinito in modo diretto o *futureonly_flag* è specificato come **futureonly**. Le nuove colonne del tipo di dati alias ereditano sempre il valore predefinito.  
  
 Quando si associa un valore predefinito a una colonna, informazioni correlate vengono aggiunte al **Columns** vista del catalogo. Quando si associa un valore predefinito a un tipo di dati alias, informazioni correlate vengono aggiunte al **Sys. Types** vista del catalogo.  
  
## <a name="permissions"></a>Permissions  
 L'utente deve proprietario della tabella oppure essere un membro del **sysadmin** ruolo predefinito del server, o **db_owner** e **db_ddladmin** ruoli predefiniti del database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-binding-a-default-to-a-column"></a>A. Associazione di un valore predefinito a una colonna  
 Il valore predefinito `today` è stato definito nel database corrente tramite l'istruzione CREATE DEFAULT, in questo esempio tale valore viene associato alla colonna `HireDate` della tabella `Employee`. Quando si aggiunge una riga alla tabella `Employee` senza specificare dati nella colonna `HireDate` la colonna include il valore predefinito `today`.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-default-to-an-alias-data-type"></a>B. Associazione di un valore predefinito a un tipo di dati alias  
 Il valore predefinito `def_ssn` e il tipo di dati alias `ssn` esistono già. Nell'esempio seguente il valore predefinito `def_ssn` viene associato a `ssn`. Il valore predefinito viene ereditato da tutte le colonne a cui è stato assegnato il tipo di dati alias `ssn` in fase di creazione della tabella. Le colonne esistenti del tipo **ssn** ereditano inoltre il valore predefinito **def_ssn**, a meno che **futureonly** specificato per *futureonly_flag* valore, a meno che la colonna ha un valore predefinito associato direttamente. I valori predefiniti associati alle colonne sono sempre prioritari rispetto a quelli associati ai tipi di dati.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonlyflag"></a>C. Utilizzo di futureonly_flag  
 Nell'esempio seguente il valore predefinito `def_ssn` viene associato al tipo di dati alias `ssn`. Poiché **futureonly** è specificato, non le colonne esistenti di tipo `ssn` sono interessate.  
  
```  
USE master;  
GO  
EXEC sp_bindefault 'def_ssn', 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D. Utilizzo di identificatori delimitati  
 Nell'esempio seguente viene illustrato l'utilizzo di identificatori delimitati, `[t.1]`nella *object_name*.  
  
```  
USE master;  
GO  
CREATE TABLE [t.1] (c1 int);   
-- Notice the period as part of the table name.  
EXEC sp_bindefault 'default1', '[t.1].c1' ;  
-- The object contains two periods;   
-- the first is part of the table name,   
-- and the second distinguishes the table name from the column name.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [ELIMINARE predefinito &#40; Transact-SQL &#41;](../../t-sql/statements/drop-default-transact-sql.md)   
 [sp_unbindefault &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
