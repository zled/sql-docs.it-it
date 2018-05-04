---
title: MSmerge_partition_groups (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_partition_groups_TSQL
- MSmerge_partition_groups
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_partition_groups system table
ms.assetid: 5d56d780-ee40-4afc-9c2a-d1723d86e430
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c9c715208d678b6bee1dbbe2a1b6b5a01f32c1cc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msmergepartitiongroups-transact-sql"></a>MSmerge_partition_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_partition_groups** tabella archivia una riga per ogni partizione in un determinato database pre-calcolata. Oltre alle colonne elencate, a questa tabella viene aggiunta una colonna per ogni funzione utilizzata in un filtro di riga con parametri. Ad esempio, una colonna denominata **HOST_NAME_FN** viene aggiunto alla tabella se viene utilizzato un filtro di [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) (funzione). Viene archiviata una riga per ogni set univoco di valori di funzione sincronizzati con il server di pubblicazione corrente. Due o più Sottoscrittori che eseguono la sincronizzazione in base allo stesso valore per tutte le funzioni dovranno condividere la stessa riga della tabella e pertanto lo stesso ID di partizione. Questa tabella è archiviata nel database di pubblicazione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|Colonna Identity che offre un numero di ID univoco per la partizione pre-calcolata.|  
|**publication_number**|**smallint**|Il numero di pubblicazione, che viene archiviato in **sysmergepublications**.|  
|**maxgen_whenadded**|**bigint**|Generazione con valore maggiore nota nel server di pubblicazione al momento dell'inserimento della riga nella tabella.|  
|**using_partition_groups**|**bit**|Indica se la partizione appartiene a una pubblicazione che utilizza partizioni pre-compilate. I possibili valori sono i seguenti.<br /><br /> **0** = pubblicazione non utilizza partizioni pre-calcolate.<br /><br /> **1** = le partizioni precalcolate di pubblicazione viene utilizzato<br /><br /> Per altre informazioni, vedere [Ottimizzare le prestazioni dei filtri con parametri con le partizioni pre-calcolate](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).|  
|**HOST_NAME_FN**|**nvarchar(128)**|Valore specificato in caso di utilizzo di filtri di riga con parametri per generare partizioni. Per altre informazioni, vedere [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
