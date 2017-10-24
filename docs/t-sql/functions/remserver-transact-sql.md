---
title: '@@REMSERVER (Transact-SQL) | Documenti Microsoft'
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
- '@@REMSERVER'
- '@@REMSERVER_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], remote servers
- remote servers [SQL Server], logins
- '@@REMSERVER function'
ms.assetid: 0bb451a9-3866-4064-963d-b74a2f864049
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: fd32b0c7ebc6da51fe50787a8492d52928dd7d32
ms.contentlocale: it-it
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40remserver-transact-sql"></a>& #x 40; & #x 40; REMSERVER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Utilizzare i server collegati e le stored procedure per i server collegati in alternativa.  
  
 Restituisce il nome del server di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] remoto così come è indicato nel record di accesso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@REMSERVER  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar (128)**  
  
## <a name="remarks"></a>Osservazioni  
 @@REMSERVER consente a una stored procedure controllare il nome del server di database da cui viene eseguita la procedura.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata la procedura `usp_CheckServer` che restituisce il nome del server remoto.  
  
```  
CREATE PROCEDURE usp_CheckServer  
AS  
SELECT @@REMSERVER;  
```  
  
 La stored procedure seguente viene creata nel server locale `SEATTLE1`. L'utente accede al server remoto `LONDON2` ed esegue la procedura `usp_CheckServer`.  
  
```  
EXEC SEATTLE1...usp_CheckServer;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------  
LONDON2  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di configurazione &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Server remoti](../../database-engine/configure-windows/remote-servers.md)  
  
  

