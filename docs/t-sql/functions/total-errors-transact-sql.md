---
title: '@@TOTAL_ERRORS (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@TOTAL_ERRORS'
- '@@TOTAL_ERRORS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@TOTAL_ERRORS function'
- total errors [SQL Server]
- errors [SQL Server], read/write
- number of disk read/write errors
- disks [SQL Server], errors
- write errors [SQL Server]
- read/write errors
ms.assetid: 09e62428-ee0e-4ef5-b969-da9d255f1199
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 83d639209d35d6516bd9348f40f4eddfd30ddff5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="totalerrors-transact-sql"></a>@@TOTAL_ERRORS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero di errori di scrittura su disco rilevati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dopo l'ultimo avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
@@TOTAL_ERRORS  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **integer**  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione non restituisce tutti gli errori di scrittura rilevati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Gli errori di scrittura occasionali e non irreversibili vengono gestiti dal server stesso e non vengono considerati errori veri e propri. Per visualizzare un report contenente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statistiche, incluso il numero totale di errori, eseguire **sp_monitor**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato il numero di errori rilevati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in corrispondenza della data e dell'ora correnti.  
  
```  
SELECT @@TOTAL_ERRORS AS 'Errors', GETDATE() AS 'As of';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Errors      As of                   
----------- ----------------------  
0           3/28/2003 12:32:11 PM   
```  
  
## <a name="see-also"></a>Vedere anche  
 [la procedura sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [Funzioni statistiche di sistema &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
