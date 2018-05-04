---
title: sp_updatestats (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 09/25/2017
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
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 0f10122f44768dd19f08f17ca9b2a12136be754f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spupdatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Esegue l'istruzione UPDATE STATISTICS su tutte le tabelle definite dall'utente e interne nel database corrente.  
  
 Per ulteriori informazioni sull'aggiornamento delle statistiche, vedere [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Per ulteriori informazioni sulle statistiche, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
    
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="arguments"></a>Argomenti  
 [ **@resample** =] **'resample'**  
 Specifica che **sp_updatestats** utilizzerà l'opzione RESAMPLE del [UPDATE STATISTICS](../../t-sql/statements/update-statistics-transact-sql.md) istruzione. Se **'resample'** non viene specificato, **sp_updatestats** Aggiorna le statistiche in base al campionamento predefinito. **RESAMPLE** viene **varchar (8)** con valore predefinito è No.  
  
## <a name="remarks"></a>Osservazioni  
 **sp_updatestats** esegue UPDATE STATISTICS, specificando la parola chiave ALL su tutte le tabelle interne e definite dall'utente nel database. sp_updatestats Visualizza i messaggi che indicano lo stato di avanzamento. Al termine dell'aggiornamento, viene segnalato che sono state aggiornate le statistiche di tutte le tabelle.  
  
 sp_updatestats aggiorna le statistiche negli indici non cluster disabilitati, mentre non le aggiorna negli indici cluster disabilitati.  
  
 Per le tabelle basate su disco, **sp_updatestats** Aggiorna le statistiche in base il **modification_counter** informazioni il **Sys.dm db_stats_properties** vista del catalogo aggiornamento delle statistiche in cui è stata modificata almeno una riga. Le statistiche sulle tabelle con ottimizzazione per la memoria vengono sempre aggiornate durante l'esecuzione di **sp_updatestats**. Pertanto, non eseguire **sp_updatestats** più del necessario.  
  
 **sp_updatestats** può attivare una ricompilazione della stored procedure o altro codice compilato. Tuttavia, **sp_updatestats** potrebbe non causare una ricompilazione, se solo un piano di query è possibile per le tabelle a cui fa riferimento e gli indici su di essi. Una ricompilazione non sarebbe necessaria in tali casi anche se le statistiche vengono aggiornate.  
  
 Per i database con un livello di compatibilità inferiore a 90, l'esecuzione **sp_updatestats** non mantiene l'impostazione più recente di NORECOMPUTE per statistiche specifiche. Per i database con un livello di compatibilità 90 o superiore, sp_updatestats mantiene il più recente di NORECOMPUTE per statistiche specifiche. Per altre informazioni sulla disabilitazione e sulla riabilitazione degli aggiornamenti delle statistiche, vedere [Statistiche](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **sysadmin** fissa ruolo del server o il proprietario del database (**dbo**).  
  
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
  
  
