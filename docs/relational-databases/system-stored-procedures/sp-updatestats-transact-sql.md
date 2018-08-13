---
title: sp_updatestats (Transact-SQL) | Documenti di Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_updatestats_TSQL
- sp_updatestats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatestats
ms.assetid: 01184651-6e61-45d9-a502-366fecca0ee4
caps.latest.revision: 45
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: cd4eada4db6af75ad794efdba231407b23f79354
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39560581"
---
# <a name="spupdatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Esegue l'istruzione UPDATE STATISTICS su tutte le tabelle definite dall'utente e interne nel database corrente.  
  
 Per ulteriori informazioni sull'aggiornamento delle statistiche, vedere [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Per altre informazioni sulle statistiche, vedere [Statistiche](../../relational-databases/statistics/statistics.md).  
    
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="arguments"></a>Argomenti  
 [ **@resample** =] **'immagini'**  
 Specifica che **sp_updatestats** utilizzerà l'opzione RESAMPLE della [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) istruzione. Se **'ricampionamento'** non è specificato, **sp_updatestats** Aggiorna le statistiche tramite il campionamento predefinito. **ricampionare** è **varchar (8)** con un valore predefinito del campo Nr.  
  
## <a name="remarks"></a>Note  
 **sp_updatestats** esegue UPDATE STATISTICS, specificando la parola chiave ALL, tutte le tabelle interne e definiti dall'utente nel database. sp_updatestats Visualizza messaggi che indicano lo stato di avanzamento. Al termine dell'aggiornamento, viene segnalato che sono state aggiornate le statistiche di tutte le tabelle.  
  
 sp_updatestats aggiorna le statistiche negli indici non cluster disabilitati, mentre non le aggiorna negli indici cluster disabilitati.  
  
 Per le tabelle basate su disco, **sp_updatestats** Aggiorna le statistiche in base la **modification_counter** informazioni di **sys.dm_db_stats_properties** , visualizzazione catalogo aggiornamento delle statistiche in almeno una riga è stata modificata. Statistiche sulle tabelle di memoria ottimizzato vengono sempre aggiornate durante l'esecuzione di **sp_updatestats**. Pertanto non vengono eseguiti **sp_updatestats** più del necessario.  
  
 **sp_updatestats** consente di attivare la ricompilazione di stored procedure o altro codice compilato. Tuttavia, **sp_updatestats** potrebbe non provocare una ricompilazione, se solo un piano di query è possibile che le tabelle di riferimento e gli indici su di essi. Una ricompilazione non sarebbe necessaria in tali casi anche se le statistiche vengono aggiornate.  
  
 Per i database con un livello di compatibilità inferiore a 90, esecuzione di **sp_updatestats** non mantiene l'ultima impostazione NORECOMPUTE statistiche specifiche. Per i database con un livello di compatibilità di 90 o superiore, sp_updatestats mantenere l'opzione NORECOMPUTE più recente per statistiche specifiche. Per altre informazioni sulla disabilitazione e sulla riabilitazione degli aggiornamenti delle statistiche, vedere [Statistiche](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Permissions  
 È necessario appartenere al **sysadmin** fissa il ruolo di server o proprietà del database (**dbo**).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono aggiornate le statistiche per le tabelle del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Stored procedure di sistema](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
