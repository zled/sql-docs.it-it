---
title: '@@IO_BUSY (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@IO_BUSY'
- '@@IO_BUSY_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- ticks [SQL Server]
- I/O [SQL Server], time spent performing operations
- '@@IO_BUSY function'
- output operations [SQL Server]
- input operations [SQL Server]
- time [SQL Server], I/O operations
ms.assetid: 3c26770c-41ae-4e34-8c82-7bef920ffbca
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 48e1bcd5a80825715ad6aed8649dad843e92c1ea
ms.contentlocale: it-it
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40iobusy-transact-sql"></a>& #x 40; & #x 40; IO_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il periodo di tempo impiegato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'esecuzione di operazioni di input e di output dopo l'avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il risultato è in incrementi di tempo di CPU, o "tick" ed è cumulativo per tutte le CPU, pertanto può essere maggiore del tempo trascorso effettivo. Moltiplicare per@TIMETICKS per convertire i microsecondi.  
  
> [!NOTE]  
>  Se l'ora restituita@CPU_BUSY, o @@IO_BUSY superiore a circa 49 giorni di tempo cumulativo di CPU, viene visualizzato un avviso di overflow aritmetico. In questo caso, il valore di @@CPU_BUSY, @@IO_BUSY e @@IDLE variabili non sono precise.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@IO_BUSY  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **integer**  
  
## <a name="remarks"></a>Osservazioni  
 Per visualizzare un report contenente dati statistici relativi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], eseguire la procedura sp_monitor.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il numero di millisecondi impiegati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'esecuzione di operazioni di input e di output tra l'ora di avvio e l'ora corrente. Per evitare l'overflow aritmetico durante la conversione del valore in microsecondi, l'esempio consente di convertire uno dei valori per il **float** tipo di dati.  
  
```  
SELECT @@IO_BUSY*@@TIMETICKS AS 'IO microseconds',   
   GETDATE() AS 'as of';  
```  
  
 Quello che segue è un set di risultati tipico:  
  
```  
  
IO microseconds as of                   
--------------- ----------------------  
4552312500      12/5/2006 10:23:00 AM   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys.dm os_sys_info &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [@@CPU_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [la procedura sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Funzioni statistiche di sistema &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  

