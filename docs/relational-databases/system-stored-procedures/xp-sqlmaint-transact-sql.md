---
title: xp_sqlmaint (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- xp_sqlmaint
- xp_sqlmaint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sqlmaint
ms.assetid: bda66e1b-6bbd-49be-b86e-37efc920e912
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c127d8cf7e27872d946a350c3e5d53e900145805
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="xpsqlmaint-transact-sql"></a>xp_sqlmaint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Chiamate di **sqlmaint** utilità con una stringa che contiene **sqlmaint**commutatori. Il **sqlmaint** utilità esegue una serie di operazioni di manutenzione su uno o più database.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
xp_sqlmaint 'switch_string'     
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *switch_string* **'**  
 È una stringa contenente il **sqlmaint** opzioni dell'utilità. Le opzioni e i relativi valori devono essere separati da uno spazio.  
  
 Il **-?** opzione non è valida per **xp_sqlmaint**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno Restituisce un errore se il **sqlmaint** ha esito negativo di utilità.  
  
## <a name="remarks"></a>Osservazioni  
 Se questa procedura viene chiamata da un utente l'accesso con autenticazione di SQL Server, il **- U "***login_id***"** e **-P "***password***"** switch vengono anteposti *switch_string* prima dell'esecuzione. Se l'utente è connesso con l'autenticazione di Windows, *switch_string* viene passato senza apportare modifiche **sqlmaint**.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente `xp_sqlmaint` viene chiamata da `sqlmaint` per eseguire controlli di integrità, creare un file di report e aggiornare `msdb.dbo.sysdbmaintplan_history`.  
  
```  
EXEC xp_sqlmaint '-D AdventureWorks2012 -PlanID 02A52657-D546-11D1-9D8A-00A0C9054212   
   -Rpt "C:\Program Files\Microsoft SQL Server\MSSQL\LOG\DBMaintPlan2.txt" -WriteHistory  -CkDB -CkAl';   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The command(s) executed successfully.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità sqlmaint](../../tools/sqlmaint-utility.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
