---
title: sp_helpconstraint (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpconstraint
- sp_helpconstraint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpconstraint
ms.assetid: 29d6cd36-535d-4765-bca8-62f9d9886ff5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4d7ef47ca294a7f52c59fa16755d316d1e574e9e
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sphelpconstraint-transact-sql"></a>sp_helpconstraint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un elenco di tutti i tipi di vincoli, con i relativi nomi definiti dall'utente o dal sistema, le colonne in cui sono stati definiti e l'espressione che li definisce (solo per i vincoli DEFAULT e CHECK).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpconstraint [ @objname = ] 'table'   
     [ , [ @nomsg = ] 'no_message' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@objname=** ] **'***tabella***'**  
 Tabella di cui si desidera ottenere informazioni sui vincoli. La tabella specificata deve essere locale rispetto al database corrente. *tabella* è **nvarchar(776)**, non prevede alcun valore predefinito.  
  
 [  **@nomsg=**] **'***no_message***'**  
 Parametro facoltativo che consente di stampare il nome della tabella. *no_message* è **varchar (5)**, il valore predefinito è **msg**. **nomsg** Annulla la stampa.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 **sp_helpconstraint** Visualizza colonne indicizzate in ordine decrescente, se fanno parte di chiavi primarie. Nel set di risultati il nome di tali colonne viene seguito da un segno meno (-). Nel caso di colonne indicizzate in ordine crescente, come per impostazione predefinita, viene invece visualizzato solo il nome delle colonne.  
  
## <a name="remarks"></a>Osservazioni  
 L'esecuzione di **sp_help***tabella* tutte le informazioni sulla tabella specificata. Per visualizzare solo le informazioni sui vincoli, utilizzare **sp_helpconstraint**.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono illustrati tutti i vincoli per la tabella `Product`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpconstraint 'Production.Product';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Sys. key_constraints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [Sys. CHECK_CONSTRAINTS &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [default_constraints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md)  
  
  
