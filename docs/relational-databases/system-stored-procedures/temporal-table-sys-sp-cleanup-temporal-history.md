---
title: Sys.sp_cleanup_temporal_history | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.service: sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
caps.latest.revision: 4
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: ebea6e162bb047f6c6224001e70dede74b5d58cc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysspcleanuptemporalhistory-transact-sql"></a>Sys.sp_cleanup_temporal_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

Rimuove tutte le righe dalla tabella di cronologia temporale che corrispondono a periodo HISTORY_RETENTION configurato all'interno di una singola transazione.
  
## <a name="syntax"></a>Sintassi  
```  
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```  
  
## <a name="arguments"></a>Argomenti  

*@table_name*

Il nome della tabella temporale per cui la conservazione pulizia viene richiamata.

*schema_name*

Il nome dello schema a cui appartiene la tabella temporale corrente

*row_count_var* [OUTPUT]

Il parametro di output che restituisce i numero di righe eliminate. Se la tabella di cronologia è inserito nel cluster indice columnstore, questo parametro restituirà sempre 0.
  
## <a name="remarks"></a>Osservazioni
Questa stored procedure è utilizzabile solo con le tabelle temporali di periodo di memorizzazione finito specificato.
Utilizzare questa stored procedure solo se è necessario eliminare immediatamente tutte le righe obsolete dalla tabella di cronologia. È necessario sapere che può avere un impatto significativo sul log del database e il sottosistema dei / o come Elimina tutte le righe idonee nella stessa transazione. 

È sempre consigliabile si basano su un'attività in background interno per la pulizia che rimuove obsoleti righe con un impatto minimo sul database in generale e carichi di lavoro normali.

## <a name="permissions"></a>Autorizzazioni  
 Richiede autorizzazioni db_owner.  

## <a name="example"></a>Esempio

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>Vedere anche

[Criteri di conservazione di tabelle temporali](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
