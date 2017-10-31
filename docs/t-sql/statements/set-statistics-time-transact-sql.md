---
title: SET STATISTICS TIME (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_TIME_TSQL
- SET STATISTICS TIME
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], statement processing
- time [SQL Server], statement processing statistics
- SET STATISTICS TIME statement
- STATISTICS TIME option
- statements [SQL Server], statistical information
- parsing [SQL Server], SET STATISTICS TIME statement
- compile times [SQL Server]
- execution processing time [SQL Server]
ms.assetid: eec2e1cd-a29d-4cf3-a271-be9d61506f15
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: acd4684ea6b44f3a7371424eb6c90305e78841fc
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="set-statistics-time-transact-sql"></a>SET STATISTICS TIME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Visualizza il numero di millisecondi necessari per l'analisi, la compilazione e l'esecuzione di ogni istruzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET STATISTICS TIME { ON | OFF }  
```  
  
## <a name="remarks"></a>Osservazioni  
 Quando l'opzione SET STATISTICS TIME è impostata su ON, vengono visualizzate le statistiche temporali di un'istruzione. Quando è impostata su OFF, le statistiche temporali non vengono visualizzate.  
  
 L'opzione SET STATISTICS TIME viene impostata in fase di esecuzione, non in fase di analisi.  
  
 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in grado di fornire statistiche accurate in modalità fiber, che viene attivata quando si abilita il **il lightweight pooling** opzione di configurazione.  
  
 Il **cpu** colonna il **sysprocesses** tabella viene aggiornata solo quando si esegue una query con SET STATISTICS TIME ON. Quando SET STATISTICS TIME è impostata su OFF, **0** viene restituito.  
  
 Le impostazioni ON e OFF hanno inoltre effetto sulla colonna CPU nella visualizzazione Informazioni processo nell'Attività corrente in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Permissions  
 Per utilizzare SET STATISTICS TIME, gli utenti devono disporre delle autorizzazioni appropriate per eseguire l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)]. Non sarà necessario disporre dell'autorizzazione SHOWPLAN.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono visualizzati i tempi di esecuzione, analisi e compilazione del server.  
  
```  
USE AdventureWorks2012;  
GO         
SET STATISTICS TIME ON;  
GO  
SELECT ProductID, StartDate, EndDate, StandardCost   
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET STATISTICS TIME OFF;  
GO  
```  
  
 Set di risultati:  
  
```  
SQL Server parse and compile time:   
   CPU time = 0 ms, elapsed time = 1 ms.  
SQL Server parse and compile time:   
   CPU time = 0 ms, elapsed time = 1 ms.  
  
(269 row(s) affected)  
  
SQL Server Execution Times:  
   CPU time = 0 ms,  elapsed time = 2 ms.  
SQL Server parse and compile time:   
   CPU time = 0 ms, elapsed time = 1 ms.  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET STATISTICS IO &#40; Transact-SQL &#41;](../../t-sql/statements/set-statistics-io-transact-sql.md)  
  
  

