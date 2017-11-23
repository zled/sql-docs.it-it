---
title: sp_helptext (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sp_helptext
- sp_helptext_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helptext
ms.assetid: 24135456-05f0-427c-884b-93cf38dd47a8
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5bb1040ec0d02d207b6b5e78892571d9cacd3275
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelptext-transact-sql"></a>sp_helptext (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Visualizza la definizione di una regola definita dell'utente, un valore predefinito, una stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] non crittografata, una funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] definita dall'utente, un trigger, una colonna calcolata, un vincolo CHECK, una vista oppure un oggetto di sistema quale una stored procedure di sistema.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helptext [ @objname = ] 'name' [ , [ @columnname = ] computed_column_name ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@objname =** ] **'***nome***'**  
 Nome completo o nome non qualificato di un oggetto con ambito schema definito dall'utente. Le virgolette sono necessarie solo se viene specificato un oggetto qualificato. Nel caso di un nome completo, ovvero contenente un nome di database, il nome del database deve corrispondere a quello del database corrente. L'oggetto deve essere presente nel database corrente. *nome* è **nvarchar(776)**, non prevede alcun valore predefinito.  
  
 [  **@columnname =** ] **'***computed_column_name***'**  
 Nome della colonna calcolata su cui si desidera ottenere informazioni di definizione. La tabella che contiene la colonna deve essere specificata come *nome*. *column_name* è **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**Text**|**nvarchar(255)**|Definizione dell'oggetto|  
  
## <a name="remarks"></a>Osservazioni  
 sp_helptext visualizza la definizione utilizzata per creare un oggetto in più righe. Ogni riga include 255 caratteri della definizione [!INCLUDE[tsql](../../includes/tsql-md.md)]. La definizione si trova nel **definizione** colonna il [Sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) vista del catalogo.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** . Le definizioni degli oggetti di sistema sono visibili pubblicamente. La definizione degli oggetti utente è visibile al proprietario degli oggetti o agli utenti autorizzati che dispongono di una delle autorizzazioni seguenti: ALTER, CONTROL, TAKE OWNERSHIP o VIEW DEFINITION.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-displaying-the-definition-of-a-trigger"></a>A. Visualizzazione della definizione di un trigger  
 Nell'esempio seguente viene visualizzata la definizione del trigger `dEmployee` nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptext 'HumanResources.dEmployee';  
GO  
```  
  
### <a name="b-displaying-the-definition-of-a-computed-column"></a>B. Visualizzazione della definizione di una colonna calcolata  
 Nell'esempio seguente viene visualizzata la definizione della colonna calcolata `TotalDue` nella tabella `SalesOrderHeader` del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
sp_helptext @objname = N'AdventureWorks2012.Sales.SalesOrderHeader', @columnname = TotalDue ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Text`  
  
 `---------------------------------------------------------------------`  
  
 `(isnull(([SubTotal]+[TaxAmt])+[Freight],(0)))`  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
