---
title: '@@IDLE (Transact-SQL) | Documenti Microsoft'
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
- '@@IDLE_TSQL'
- '@@IDLE'
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], idle
- ticks [SQL Server]
- '@@IDLE function'
- status information [SQL Server], idle time
- idle time [SQL Server]
ms.assetid: 8f49c62a-8da5-4afd-a5eb-4df8ef8be755
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: ab308bcb1fd3ffdda8e901b2238111abaddecb81
ms.contentlocale: it-it
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40idle-transact-sql"></a>& #x 40; & #x 40; inattivo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il periodo di tempo in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è rimasto inattivo dopo l'ultimo avvio. Il risultato è in incrementi di tempo di CPU, o "tick" ed è cumulativo per tutte le CPU, pertanto può essere maggiore del tempo trascorso effettivo. Moltiplicare per@TIMETICKS per convertire i microsecondi.  
  
> [!NOTE]  
>  Se l'ora restituita@CPU_BUSY, o @@IO_BUSY superiore a circa 49 giorni di tempo cumulativo di CPU, viene visualizzato un avviso di overflow aritmetico. In questo caso, il valore di @@CPU_BUSY, @@IO_BUSY e @@IDLE variabili non sono precise.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@IDLE  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **integer**  
  
## <a name="remarks"></a>Osservazioni  
 Per visualizzare un report contenente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statistiche, eseguire **sp_monitor**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il numero di millisecondi di inattività di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trascorsi tra l'ora di avvio e l'ora corrente. Per evitare un overflow aritmetico durante la conversione del valore in microsecondi, uno dei valori viene convertito nel tipo di dati `float`.  
  
```  
SELECT @@IDLE * CAST(@@TIMETICKS AS float) AS 'Idle microseconds',  
   GETDATE() AS 'as of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
I  
Idle microseconds  as of                   
----------------- ----------------------  
8199934           12/5/2006 10:23:00 AM   
```  
  
## <a name="see-also"></a>Vedere anche  
 [@@CPU_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [la procedura sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [@@IO_BUSY &#40;Transact-SQL&#41;](../../t-sql/functions/io-busy-transact-sql.md)   
 [Funzioni statistiche di sistema &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  

