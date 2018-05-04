---
title: sp_helpstats (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpstats
- sp_helpstats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpstats
ms.assetid: 00ab3cfd-2736-4fc0-b1b2-16dd49fb2fe5
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d5f26feb376b8c671e4b98d4524e7491d719c3d8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpstats-transact-sql"></a>sp_helpstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni statistiche sulle colonne e gli indici della tabella specificata.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] Per ottenere informazioni sulle statistiche, eseguire una query di [Sys. Stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) e [Sys. stats_columns](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md) viste del catalogo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpstats[ @objname = ] 'object_name'   
     [ , [ @results = ] 'value' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@objname=**] **'***object_name***'**  
 Specifica la tabella per cui recuperare le informazioni statistiche. *object_name* viene **nvarchar(520)** e non può essere null. È possibile specificare un nome composto da una o due parti.  
  
 [  **@results=**] **'***valore***'**  
 Specifica la quantità di informazioni da restituire. Le voci valide sono **tutti** e **statistiche**. **Tutti i** Elenca le statistiche per tutti gli indici e anche le colonne con statistiche create su di essi; **STATS** solo le statistiche non associate a un indice. *valore* viene **nvarchar(5** con un valore predefinito è STATS.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nella tabella seguente vengono descritte le colonne del set di risultati.  
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|**statistics_name**|Nome delle statistiche. Restituisce **sysname** e non può essere null.|  
|**statistics_keys**|Chiavi su cui sono basate le statistiche. Restituisce **nvarchar(2078)** e non può essere null.|  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare DBCC SHOW_STATISTICS per visualizzare informazioni statistiche dettagliate su indici o statistiche specifici. Per altre informazioni, vedere [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41; ](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md) e [sp_helpindex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono create statistiche a colonna singola per tutte le colonne appropriate di tutte le tabelle utente nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] eseguendo la stored procedure `sp_createstats`. Viene poi eseguita la stored procedure `sp_helpstats` per recuperare le statistiche risultanti create nella tabella `Customer`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_createstats;  
GO  
EXEC sp_helpstats   
@objname = 'Sales.Customer',  
@results = 'ALL';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `statistics_name               statistics_keys`  
  
 `----------------------------  ----------------`  
  
 `_WA_Sys_00000003_22AA2996     AccountNumber`  
  
 `AK_Customer_AccountNumber     AccountNumber`  
  
 `AK_Customer_rowguid           rowguid`  
  
 `CustomerType                  CustomerType`  
  
 `IX_Customer_TerritoryID       TerritoryID`  
  
 `ModifiedDate                  ModifiedDate`  
  
 `PK_Customer_CustomerID        CustomerID`  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure del motore di database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
