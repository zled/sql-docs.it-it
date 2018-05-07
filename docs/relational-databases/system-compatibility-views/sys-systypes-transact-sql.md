---
title: systypes (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.systypes_TSQL
- systypes_TSQL
- sys.systypes
- systypes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.systypes compatibility view
- systypes system table
ms.assetid: 1b0b1d0c-5f7b-470b-bd52-8bfa922d7889
caps.latest.revision: 50
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8526b0335d9d222cd0c28f4304566812905a07b7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="syssystypes-transact-sql"></a>sys.systypes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni tipo di dati di sistema o definito dall'utente nel database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del tipo di dati.|  
|**tipoX**|**tinyint**|Tipo di dati per l'archiviazione fisica.|  
|**status**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|Tipo di dati esteso definito dall'utente. Causa un errore di overflow o restituisce NULL se il numero di tipi di dati è maggiore di 32.767.|  
|**lunghezza**|**smallint**|Lunghezza fisica del tipo di dati.|  
|**xprec**|**tinyint**|Precisione interna utilizzata dal server, da non utilizzare nelle query.|  
|**XScale**|**tinyint**|Scala interna utilizzata dal server, da non utilizzare nelle query.|  
|**TImpossibile**|**int**|ID della stored procedure che include i controlli di integrità per questo tipo di dati.|  
|**domain**|**int**|ID della stored procedure che include i controlli di integrità per questo tipo di dati.|  
|**uid**|**smallint**|ID dello schema del proprietario del tipo.<br /><br /> Per i database aggiornati da una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'ID dello schema corrisponde all'ID utente del proprietario.<br /><br /> **\*\* Importante \* \***  se si usa uno dei seguenti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le istruzioni DDL, è necessario utilizzare il [Types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) invece di vista del catalogo **systypes**.<br /><br /> ALTER AUTHORIZATION ON TYPE<br /><br /> CREATE TYPE<br /><br /> Causa un errore di overflow o restituisce NULL se il numero di utenti e ruoli è maggiore di 32.767.|  
|**reserved**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**collationid**|**int**|Se di tipo carattere, **collationid** è l'id delle regole di confronto del database corrente; in caso contrario, è NULL.|  
|**usertype**|**smallint**|ID tipo utente. Causa un errore di overflow o restituisce NULL se il numero di tipi di dati è maggiore di 32.767.|  
|**variable**|**bit**|Tipo di dati a lunghezza variabile.<br /><br /> 1 = True<br /><br /> 0 = False|  
|**AllowNulls**|**bit**|Indica l'impostazione predefinita relativa al supporto dei valori Null per questo tipo di dati. Il valore predefinito viene ignorato, se l'ammissione di valori null specificato tramite [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) o [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).|  
|**type**|**tinyint**|Tipo di dati per l'archiviazione fisica.|  
|**printfmt**|**varchar(255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Prec**|**smallint**|Livello di precisione per il tipo di dati.<br /><br /> -1 = **xml** o tipi di valori di grandi dimensioni.|  
|**scala**|**tinyint**|Scala per il tipo di dati, basata sulla precisione.<br /><br /> NULL = Tipo di dati non numerico.|  
|**Regole di confronto**|**sysname**|Se di tipo carattere, **delle regole di confronto** è le regole di confronto del database corrente; in caso contrario, è NULL.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
