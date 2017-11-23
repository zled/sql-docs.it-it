---
title: DISABLE TRIGGER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DISABLE_TSQL
- DISABLE
- DISABLE TRIGGER
- DISABLE_TRIGGER_TSQL
dev_langs: TSQL
helpviewer_keywords:
- DML triggers, disabling
- DDL triggers, disabling
- DISABLE TRIGGER statement
- triggers [SQL Server], disabling
- disabling triggers
ms.assetid: e6529f06-e442-437e-a7bf-41790bc092c5
caps.latest.revision: "45"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 69398e740c4ae5ca49c93b1f70d7c02a0d3fbf42
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="disable-trigger-transact-sql"></a>DISABLE TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Consente di disabilitare un trigger.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DISABLE TRIGGER { [ schema_name . ] trigger_name [ ,...n ] | ALL }  
ON { object_name | DATABASE | ALL SERVER } [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *schema_name*  
 Nome dello schema a cui appartiene il trigger. *schema_name* non può essere specificato per i trigger DDL o logon.  
  
 *trigger_name*  
 Nome del trigger che si desidera disabilitare.  
  
 ALL  
 Disabilita tutti i trigger con l'ambito specificato nella clausola ON.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crea trigger nei database pubblicati per la replica di tipo merge. Se si specifica ALL nei database pubblicati, questi trigger vengono disabilitati e la replica viene ostacolata. Prima di utilizzare l'argomento ALL verificare che il database corrente non sia pubblicato per la replica di tipo merge.  
  
 *object_name*  
 È il nome della tabella o della vista in cui il trigger DML *trigger_name* è stato creato per l'esecuzione.  
  
 DATABASE  
 Per un trigger DDL, indica che *trigger_name* è stato creato o modificato per essere eseguito con ambito database.  
  
 ALL SERVER  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Per un trigger DDL, indica che *trigger_name* è stato creato o modificato per essere eseguito con ambito server. ALL SERVER si applica anche ai trigger LOGON.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
## <a name="remarks"></a>Osservazioni  
 Per impostazione predefinita, i trigger vengono abilitati in fase di creazione. La disabilitazione di un trigger non ne comporta l'eliminazione. Il trigger continua a esistere come oggetto nel database corrente ma non viene attivato quando viene eseguita una qualsiasi istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] in cui è stato programmato. I trigger possono essere riabilitati tramite [ENABLE TRIGGER](../../t-sql/statements/enable-trigger-transact-sql.md). I trigger DML definiti nelle tabelle possono essere anche essere abilitato o disabilitato utilizzando [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 La modifica del trigger tramite la **ALTER TRIGGER** istruzione attiva il trigger.  
  
## <a name="permissions"></a>Permissions  
 Per disabilitare un trigger DML, è necessario disporre almeno dell'autorizzazione ALTER per la tabella o la vista per cui il trigger è stato creato.  
  
 Per disabilitare un trigger DDL con ambito server (ON ALL SERVER) o un trigger LOGON, è necessario disporre dell'autorizzazione CONTROL SERVER per il server. Per disabilitare un trigger DDL con ambito database (ON DATABASE), è necessario disporre almeno dell'autorizzazione ALTER ANY DATABASE DDL TRIGGER nel database corrente.  
  
## <a name="examples"></a>Esempi  
Negli esempi seguenti vengono descritti nel database AdventureWorks2012.
  
### <a name="a-disabling-a-dml-trigger-on-a-table"></a>A. Disabilitazione di un trigger DML in una tabella  
 Nell'esempio seguente viene disabilitato il trigger `uAddress` creato per la tabella `Address`.  
  
```  
DISABLE TRIGGER Person.uAddress ON Person.Address;  
GO  
```  
  
### <a name="b-disabling-a-ddl-trigger"></a>B. Disabilitazione di un trigger DDL  
 Nell'esempio seguente viene creato e quindi disabilitato un trigger DDL `safety` con ambito database.  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_TABLE, ALTER_TABLE   
AS   
   PRINT 'You must disable Trigger "safety" to drop or alter tables!'   
   ROLLBACK;  
GO  
DISABLE TRIGGER safety ON DATABASE;  
GO  
```  
  
### <a name="c-disabling-all-triggers-that-were-defined-with-the-same-scope"></a>C. Disabilitazione di tutti i trigger definiti con lo stesso ambito  
 Nell'esempio seguente vengono disabilitati tutti i trigger DDL creati nell'ambito del server.  
  
```  
DISABLE Trigger ALL ON ALL SERVER;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)  
  
  
