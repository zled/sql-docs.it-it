---
title: sp_addtype (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addtype
- sp_addtype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addtype
ms.assetid: ed72cd8e-5ff7-4084-8458-2d8ed279d817
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 96a2d930ae6c85e4da6d516d6c30d6c54a7fd3ac
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="spaddtype-transact-sql"></a>sp_addtype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un tipo di dati alias.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Uso [CREATE TYPE](../../t-sql/statements/create-type-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_addtype [ @typename = ] type,   
    [ @phystype = ] system_data_type   
    [ , [ @nulltype = ] 'null_type' ] ;  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@typename=** ] *tipo*  
 Nome del tipo di dati alias. Alias nomi dei tipi di dati deve seguire le regole per [identificatori](../../relational-databases/databases/database-identifiers.md) e devono essere univoci in ogni database. *tipo di* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@phystype=**] *system_data_type*  
 Fisico o [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fornito, il tipo di dati su cui è basato il tipo di dati alias. *system_data_type* è **sysname**e non prevede alcun valore predefinito può essere uno dei valori seguenti:  
  
||||  
|-|-|-|  
|**bigint**|**binary(n)**|**bit**|  
|**char(n)**|**datetime**|**decimal**|  
|**float**|**image**|**int**|  
|**money**|**nchar(n)**|**ntext**|  
|**numeric**|**nvarchar(n)**|**real**|  
|**smalldatetime**|**smallint**|**smallmoney**|  
|**sql_variant**|**text**|**tinyint**|  
|**uniqueidentifier**|**varbinary(n)**|**varchar(n)**|  
  
 È necessario racchiudere tra virgolette tutti i parametri che includono spazi vuoti o segni di punteggiatura. Per ulteriori informazioni sui tipi di dati disponibili, vedere [tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).  
  
 *n*  
 Valore intero non negativo che indica la lunghezza del tipo di dati scelto.  
  
 *P*  
 Valore intero non negativo che indica il numero massimo di cifre decimali che è possibile archiviare sia a sinistra che a destra del separatore decimale. Per altre informazioni, vedere [decimal e numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 *S*  
 Valore intero non negativo che indica il numero massimo di cifre decimali che è possibile archiviare a destra del separatore decimale. Deve essere minore o uguale al valore della precisione. Per altre informazioni, vedere [decimal e numeric &#40;Transact-SQL&#41;](../../t-sql/data-types/decimal-and-numeric-transact-sql.md).  
  
 [  **@nulltype =** ] **'***null_type***'**  
 Viene indicata la modalità di gestione dei valori Null per il tipo di dati alias. *null_type* viene **varchar (** 8 **)**, con un valore predefinito è NULL e deve essere racchiuso tra virgolette singole ('NULL', 'NOT NULL' o 'NONULL'). Se *null_type* non è definito in modo esplicito da **sp_addtype**, viene impostato su quello predefinito corrente. Utilizzare la funzione di sistema GETANSINULL per determinare l'impostazione predefinita corrente per il supporto dei valori Null. Questa impostazione può essere modificata tramite l'istruzione SET o ALTER DATABASE. L'impostazione relativa al supporto dei valori Null deve essere definita in modo esplicito. Se **@phystype** è **bit**, e **@nulltype** non viene specificato, il valore predefinito non è NULL.  
  
> [!NOTE]  
>  Il *null_type* parametro definisce solo i valori null per questo tipo di dati predefiniti. Se l'impostazione per il supporto dei valori Null viene definita in modo esplicito quando si utilizza il tipo di dati alias durante la creazione di tabelle, questo valore sarà prioritario rispetto all'impostazione predefinita. Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-table-transact-sql.md) e [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Il nome di un tipo di dati alias deve essere univoco all'interno del database, ma è possibile utilizzare la stessa definizione per tipi di dati alias con nomi diversi.  
  
 L'esecuzione di **sp_addtype** crea un tipo di dati alias che viene visualizzato nel **Sys. Types** vista per un database specifico del catalogo. Se il tipo di dati alias deve essere disponibile in tutti i nuovi database definiti dall'utente, aggiungerlo alla **modello**. Dopo avere creato un tipo di dati alias, è possibile utilizzarlo in un'istruzione CREATE TABLE o ALTER TABLE e associarvi valori predefiniti e regole. Tutti i tipi di dati alias scalari creati tramite **sp_addtype** sono contenuti nel **dbo** dello schema.  
  
 I tipi di dati alias ereditano le regole di confronto predefinite del database. Le regole di confronto delle colonne e variabili di tipi alias sono definite nel [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE, ALTER TABLE e DECLARE @*local_variable* istruzioni. Le modifiche apportate alle regole di confronto predefinite del database vengono applicate solo alle nuove colonne e variabili del tipo. Le regole di confronto delle colonne e delle variabili esistenti non vengono modificate.  
  
> [!IMPORTANT]  
>  Per motivi di compatibilità con le versioni precedenti, il **pubblica** ruolo del database viene concessa automaticamente l'autorizzazione REFERENCES per i tipi di dati alias creati tramite **sp_addtype**. Si noti quando vengono creati i tipi di dati alias tramite l'istruzione CREATE TYPE anziché **sp_addtype**, si verifica alcun questa assegnazione automatica.  
  
 Tipi di dati alias non possono essere definiti utilizzando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **timestamp**, **tabella**, **xml**, **varchar (max)**, **nvarchar (max)** o **varbinary (max)** tipi di dati.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **db_owner** o **db_ddladmin** ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-an-alias-data-type-that-does-not-allow-for-null-values"></a>A. Creazione di un tipo di dati alias che non consente valori Null  
 Nell'esempio seguente viene creato un tipo di dati alias denominato `ssn` (numero di previdenza sociale) basato sul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-fornito **varchar** tipo di dati. Il tipo di dati `ssn` viene utilizzato per colonne contenenti numeri di previdenza sociale a 11 cifre (999-99-9999). Questa colonna non può contenere valori NULL.  
  
 Si noti che `varchar(11)` è racchiuso tra virgolette singole in quanto contiene segni di punteggiatura (le parentesi).  
  
```  
USE master;  
GO  
EXEC sp_addtype ssn, 'varchar(11)', 'NOT NULL';  
GO  
```  
  
### <a name="b-creating-an-alias-data-type-that-allows-for-null-values"></a>B. Creazione di un tipo di dati alias che consente valori Null  
 Nell'esempio seguente viene creato un tipo di dati alias basato sul tipo di dati `datetime` e denominato `birthday` che consente valori Null.  
  
```  
USE master;  
GO  
EXEC sp_addtype birthday, datetime, 'NULL';  
```  
  
### <a name="c-creating-additional-alias-data-types"></a>C. Creazione di tipi di dati alias aggiuntivi  
 Nell'esempio seguente vengono creati due tipi di dati alias aggiuntivi, `telephone` e `fax`, per i numeri di telefono e di fax nazionali e internazionali.  
  
```  
USE master;  
GO  
EXEC sp_addtype telephone, 'varchar(24)', 'NOT NULL';  
GO  
EXEC sp_addtype fax, 'varchar(24)', 'NULL';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure del motore di database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-type-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [sp_bindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md)   
 [sp_bindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md)   
 [sp_droptype &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droptype-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_unbindefault &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)   
 [sp_unbindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
