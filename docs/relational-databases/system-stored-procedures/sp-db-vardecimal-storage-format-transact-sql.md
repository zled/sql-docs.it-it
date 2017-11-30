---
title: sp_db_vardecimal_storage_format (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sp_db_vardecimal_storage_format
- sp_db_vardecimal_storage_format_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_db_vardecimal_storage_format
- decimal data type, compressing
- compressing decimal data
- numeric data type, compressing
- database compression [SQL Server]
- table compression [SQL Server]
ms.assetid: 9920b2f7-b802-4003-913c-978c17ae4542
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9f34f4cb6fb3d09e2d2a58b6b29621b39ee28d6
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spdbvardecimalstorageformat-transact-sql"></a>sp_db_vardecimal_storage_format (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce lo stato corrente del formato di archiviazione vardecimal di un database oppure abilita il formato di archiviazione vardecimal per un database.  A partire da [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], i database utente sono sempre abilitati. L'abilitazione del formato di archiviazione vardecimal per i database è necessaria solo in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
> [!IMPORTANT]  
>  La modifica dello stato del formato di archiviazione vardecimal di un database può influire su backup e recupero, mirroring del database, sp_attach_db, log shipping e replica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_db_vardecimal_storage_format [ [ @dbname = ] 'database_name']   
    [ , [ @vardecimal_storage_format = ] { 'ON' | 'OFF' } ]   
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @dbname=] '*database_name*'  
 Nome del database per il quale deve essere modificato il formato di archiviazione. *database_name* è **sysname**, non prevede alcun valore predefinito. Se il nome del database viene omesso, viene restituito lo stato del formato di archiviazione vardecimal di tutti i database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [ @vardecimal_storage_format=] {'ON' |' DISATTIVARE '}  
 Specifica se il formato di archiviazione vardecimal è abilitato. @vardecimal_storage_format può essere ON oppure OFF. Il parametro è **varchar(3)**, non prevede alcun valore predefinito. Se viene specificato il nome di un database ma viene omesso @vardecimal_storage_format, viene restituita l'impostazione corrente del database specificato. Questo argomento non ha effetto in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o versioni successive.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Se il formato di archiviazione del database non può essere modificato, sp_db_vardecimal_storage_format restituisce un errore. Se lo stato corrente del database corrisponde a quello specificato, la stored procedure non produce alcun effetto.  
  
 Se il @vardecimal_storage_format argomento non è specificato, restituisce le colonne nome del Database e lo stato di Vardecimal.  
  
## <a name="remarks"></a>Osservazioni  
 sp_db_vardecimal_storage_format restituisce lo stato di vardecimal ma non consente di modificare tale stato.  
  
 sp_db_vardecimal_storage_format avrà esito negativo nelle circostanze seguenti:  
  
-   Non sono presenti utenti attivi nel database.  
  
-   È abilitato il mirroring del database.  
  
-   L'edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta il formato di archiviazione vardecimal.  
  
 Per modificare lo stato del formato di archiviazione vardecimal in OFF, è necessario che un database sia impostato sulla modalità di recupero con registrazione minima. In caso di impostazione di un database su tale modalità, la catena di log è interrotta. Dopo aver impostato lo stato del formato di archiviazione vardecimal su OFF, eseguire un backup completo del database.  
  
 La modifica dello stato in OFF avrà esito negativo se sono presenti tabelle in cui viene utilizzata la compressione di database di tipo vardecimal. Per modificare il formato di archiviazione di una tabella, utilizzare [sp_tableoption](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Per determinare le tabelle di un database in cui viene utilizzato il formato di archiviazione vardecimal, utilizzare la funzione `OBJECTPROPERTY` e cercare la proprietà `TableHasVarDecimalStorageFormat`, come illustrato nell'esempio seguente.  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT name, object_id, type_desc  
FROM sys.objects   
 WHERE OBJECTPROPERTY(object_id,   
   N'TableHasVarDecimalStorageFormat') = 1 ;  
GO  
```  
  
## <a name="examples"></a>Esempi  
 Tramite il codice seguente viene abilitata la compressione nel database `AdventureWorks2012`, viene verificato lo stato e quindi vengono compresse le colonne decimal e numeric della tabella `Sales.SalesOrderDetail`.  
  
```  
USE master ;  
GO  
  
EXEC sp_db_vardecimal_storage_format 'AdventureWorks2012', 'ON' ;  
GO  
  
-- Check the vardecimal storage format state for  
-- all databases in the instance.  
EXEC sp_db_vardecimal_storage_format ;  
GO  
  
USE AdventureWorks2012 ;  
GO  
  
EXEC sp_tableoption 'Sales.SalesOrderDetail', 'vardecimal storage format', 1 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
