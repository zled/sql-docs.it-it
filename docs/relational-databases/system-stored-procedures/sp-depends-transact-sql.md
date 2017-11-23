---
title: sp_depends (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
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
- sp_depends
- sp_depends_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_depends
ms.assetid: d9934590-c6ae-4936-91c3-146055ef2c57
caps.latest.revision: "41"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 361d4a9d937917da7dbe47b4cb4eb071277eb072
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spdepends-transact-sql"></a>sp_depends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza informazioni sulle dipendenze degli oggetti di database, ad esempio le viste e le procedure che dipendono da una tabella o da una vista e le tabelle e le viste da cui esse dipendono. I riferimenti agli oggetti esterni al database corrente non vengono riportati.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [Sys.dm sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md) e [Sys.dm sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md) invece.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_depends [ @objname = ] '<object>'   
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name.  
    object_name  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database.  
  
 *schema_name*  
 Nome dello schema a cui appartiene l'oggetto.  
  
 *object_name*  
 Oggetto di database di cui si desidera esaminare le dipendenze. L'oggetto può essere una tabella, una vista, una stored procedure, una funzione definita dall'utente o un trigger. o*bject_name* è **nvarchar(776)**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 **sp_depends** Visualizza due set di risultati.  
  
 Il set di risultati seguente vengono indicati gli oggetti che  *\<oggetto >* a seconda dei casi.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|Nome dell'elemento a cui è associata una dipendenza.|  
|**tipo**|**nvarchar (16)**|Tipo di elemento.|  
|**aggiornato**|**nvarchar(7)**|Specifica se l'elemento è aggiornato.|  
|**selezionato**|**nvarchar (8)**|Specifica se l'elemento viene utilizzato in un'istruzione SELECT.|  
|**colonna**|**sysname**|Colonna o parametro in cui esiste la dipendenza.|  
  
 Il set di risultati seguente vengono indicati gli oggetti che dipendono da  *\<oggetto >*.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar (257** **)**|Nome dell'elemento a cui è associata una dipendenza.|  
|**tipo**|**nvarchar (16)**|Tipo di elemento.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-dependencies-on-a-table"></a>A. Visualizzazione dell'elenco delle dipendenze da una tabella  
 Nell'esempio seguente vengono elencati gli oggetti di database che dipendono dalla tabella `Sales.Customer` inclusa nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Vengono specificati sia il nome dello schema che il nome della tabella.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_depends @objname = N'Sales.Customer' ;  
```  
  
### <a name="b-listing-dependencies-on-a-trigger"></a>B. Visualizzazione dell'elenco delle dipendenze da un trigger  
 Nell'esempio seguente vengono elencati gli oggetti di database da cui dipende il trigger `iWorkOrder`.  
  
```  
EXEC sp_depends @objname = N'AdventureWorks2012.Production.iWorkOrder' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Sys. sql_dependencies &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
