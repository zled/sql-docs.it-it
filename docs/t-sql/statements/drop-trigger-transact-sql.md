---
title: DROP TRIGGER (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP TRIGGER
- DROP_TRIGGER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- renaming triggers
- triggers [SQL Server], removing
- DDL triggers, removing
- DROP TRIGGER statement
- deleting triggers
- dropping triggers
- removing triggers
- DML triggers, removing
ms.assetid: 092d0d71-9f1e-4e38-a1c4-2487adfa5b4e
caps.latest.revision: 53
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e3ca35b2b33a60d0af5dd31467f1381402f8f99b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-trigger-transact-sql"></a>DROP TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Rimuove uno o più trigger DML o DDL dal database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  
  
DROP TRIGGER [ IF EXISTS ] [schema_name.]trigger_name [ ,...n ] [ ; ]  
  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, REVOKE or UPDATE statement (DDL Trigger)  
  
DROP TRIGGER [ IF EXISTS ] trigger_name [ ,...n ]   
ON { DATABASE | ALL SERVER }   
[ ; ]  
  
-- Trigger on a LOGON event (Logon Trigger)  
  
DROP TRIGGER [ IF EXISTS ] trigger_name [ ,...n ]   
ON ALL SERVER  
```  

  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658), [!INCLUDE[sssds](../../includes/sssds-md.md)]).  
  
 Elimina in modo condizionale il trigger solo se esiste già.  
  
 *schema_name*  
 Nome dello schema a cui appartiene un trigger DML. L'ambito dei trigger DML è definito nello schema della tabella o della vista in cui sono i trigger stessi creati. *schema_name* non può essere specificato per i trigger DDL o logon.  
  
 *trigger_name*  
 Nome del trigger da rimuovere. Per visualizzare un elenco dei trigger attualmente creati, utilizzare [Sys. server_assembly_modules](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) o [server_triggers](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md).  
  
 DATABASE  
 Indica che l'ambito del trigger DDL corrisponde al database corrente. È necessario specificare DATABASE se tale argomento è stato specificato anche al momento della creazione o della modifica del trigger.  
  
 ALL SERVER  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Indica che l'ambito del trigger DDL corrisponde al server corrente. È necessario specificare ALL SERVER se tale valore è stato specificato anche al momento della creazione o della modifica del trigger. ALL SERVER si applica anche ai trigger LOGON.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile rimuovere un trigger DML eliminando il trigger stesso o la tabella di trigger corrispondente. Quando si elimina una tabella, vengono eliminati anche tutti i trigger associati.  
  
 Quando viene eliminato un trigger, informazioni sul trigger viene rimosso dal **Sys. Objects**, **Triggers** e **Sys. sql_modules** viste del catalogo.  
  
 È possibile eliminare più trigger DDL con una singola istruzione DROP TRIGGER solo se tutti i trigger sono stati creati con clausole ON identiche.  
  
 Per rinominare un trigger, utilizzare le istruzioni DROP TRIGGER e CREATE TRIGGER. Per modificare la definizione di un trigger, utilizzare ALTER TRIGGER.  
  
 Per ulteriori informazioni sulla determinazione delle dipendenze per un trigger specifico, vedere [Sys. sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md), [Sys.dm sql_referenced_entities &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md), e [Sys.dm sql_referencing_entities &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md).  
  
 Per ulteriori informazioni sulla visualizzazione del testo del trigger, vedere [sp_helptext &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md) e [Sys. sql_modules &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md).  
  
 Per ulteriori informazioni sulla visualizzazione di un elenco di trigger esistenti, vedere [Triggers &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) e [server_triggers &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Per l'eliminazione di un trigger DML è richiesta l'autorizzazione ALTER per la tabella o la vista in cui è definito il trigger.  
  
 Per eliminare un trigger DDL definito con ambito server (ON ALL SERVER) o un trigger LOGON è necessaria l'autorizzazione CONTROL SERVER nel server. Per l'eliminazione di un trigger DDL con ambito database (ON DATABASE) è richiesta l'autorizzazione ALTER ANY DATABASE DDL TRIGGER nel database corrente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-a-dml-trigger"></a>A. Eliminazione di un trigger DML  
 Nell'esempio seguente viene eliminato il trigger `employee_insupd` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. (A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] è possibile utilizzare la sintassi DROP TRIGGER IF EXISTS.)  
  
```  
IF OBJECT_ID ('employee_insupd', 'TR') IS NOT NULL  
   DROP TRIGGER employee_insupd;  
```  
  
### <a name="b-dropping-a-ddl-trigger"></a>B. Eliminazione di un trigger DDL  
 Nell'esempio seguente viene eliminato il trigger DDL `safety`.  
  
> [!IMPORTANT]  
>  Poiché i trigger DDL non sono con ambito schema e, pertanto non vengono visualizzati il **Sys. Objects** vista del catalogo non è possibile utilizzare la funzione OBJECT_ID per eseguire una query se esistono nel database. Per gli oggetti che non hanno ambito schema è necessario eseguire query nella vista del catalogo appropriata. Per i trigger DDL, utilizzare **Triggers**.  
  
```  
DROP TRIGGER safety  
ON DATABASE;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Ottieni informazioni sui trigger DML](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  

