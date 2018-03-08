---
title: Transactions (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Transactions
- Transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactions [SQL Server]
- transactions [SQL Server], about transactions
- UOW [SQL Server]
- unit of work [SQL Server]
ms.assetid: 1485c375-921a-42af-a871-bb333cc08d3e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 360d2d4d88280a011687dfb3845f1de86513bdc8
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="transactions-transact-sql"></a>Transazioni (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Una transazione corrisponde a una singola unità di lavoro. Se la transazione viene eseguita correttamente, viene eseguito il commit di tutte le modifiche dei dati apportate durante la transazione e tali modifiche diventano parte permanente del database. Se si verificano errori durante l'esecuzione della transazione ed è necessario annullarla o eseguirne il rollback, verranno cancellate tutte le modifiche dei dati.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]funziona in modalità di transazione seguenti:  
  
 Transazioni con autocommit  
 Ogni istruzione corrisponde a una transazione.  
  
 Transazioni esplicite  
 Ogni transazione viene avviata in modo esplicito tramite l'istruzione BEGIN TRANSACTION e terminata con un'istruzione esplicita COMMIT o ROLLBACK.  
  
 Transazioni implicite  
 Una nuova transazione viene avviata in modo implicito al termine di una transazione precedente, ma tutte le transazioni vengono terminate in modo esplicito con un'istruzione COMMIT o ROLLBACK.  
  
 Transazioni definite a livello di ambito di batch  
 Applicabile solo a MARS (Multiple Active Result Set). Una transazione definita a livello di ambito di batch è una transazione [!INCLUDE[tsql](../../includes/tsql-md.md)] esplicita o implicita che inizia in una sessione MARS. Se per una transazione definita a livello di ambito di batch non è stato eseguito il commit o il rollback quando il batch è completato, il rollback viene eseguito automaticamente da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

> [!NOTE] 
> Per considerazioni speciali relative ai prodotti di Data Warehouse, vedere [transazioni (SQL Data Warehouse)](transactions-sql-data-warehouse.md).   

## <a name="in-this-section"></a>Contenuto della sezione  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]fornisce le seguenti istruzioni transaction:  
  
|||  
|-|-|  
|[BEGIN DISTRIBUTED TRANSACTION](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)|[ROLLBACK TRANSACTION](../../t-sql/language-elements/rollback-transaction-transact-sql.md)|  
|[BEGIN TRANSACTION](../../t-sql/language-elements/begin-transaction-transact-sql.md)|[ROLLBACK WORK](../../t-sql/language-elements/rollback-work-transact-sql.md)|  
|[COMMIT TRANSACTION](../../t-sql/language-elements/commit-transaction-transact-sql.md)|[SAVE TRANSACTION](../../t-sql/language-elements/save-transaction-transact-sql.md)|  
|[COMMIT WORK](../../t-sql/language-elements/commit-work-transact-sql.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
