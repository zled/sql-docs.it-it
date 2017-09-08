---
title: '@@LOCK_TIMEOUT (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@LOCK_TIMEOUT'
- '@@LOCK_TIMEOUT_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- timeout options [SQL Server], locks
- '@@LOCK_TIMEOUT function'
- current lock time-out setting
- locking [SQL Server], time-outs
ms.assetid: 6bf8bf97-60b8-40c1-b89d-8f5a00bcae2e
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 15ee9c5789ea6f1c7bbad6fc8caeabab14f3df4f
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="locktimeout-transact-sql"></a>@@LOCK_TIMEOUT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce l'impostazione corrente del timeout del blocco, in millisecondi, per la sessione corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
@@LOCK_TIMEOUT  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **integer**  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione SET LOCK_TIMEOUT consente a un'applicazione di impostare il periodo di tempo massimo durante il quale un'istruzione rimane in attesa di una risorsa bloccata. Quando il periodo di attesa di un'istruzione supera il valore massimo impostato con l'opzione LOCK_TIMEOUT, l'istruzione bloccata viene annullata automaticamente e nell'applicazione viene restituito un messaggio di errore.  
  
 @@LOCK_TIMEOUT restituisce un valore di -1 se SET LOCK_TIMEOUT non è ancora stato eseguito nella sessione corrente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato il set di risultati ottenuto quando per l'opzione LOCK_TIMEOUT non è stato impostato alcun valore.  
  
```  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 Set di risultati:  
  
```  
Lock Timeout  
------------  
-1  
```  
  
 In questo esempio imposta LOCK_TIMEOUT su 1800 millisecondi e quindi chiama@LOCK_TIMEOUT.  
  
```  
SET LOCK_TIMEOUT 1800;  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 Set di risultati:  
  
```  
Lock Timeout  
------------  
1800          
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di configurazione &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SET LOCK_TIMEOUT &#40; Transact-SQL &#41;](../../t-sql/statements/set-lock-timeout-transact-sql.md)  
  
  
