---
title: '@@SERVERNAME (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 09/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@SERVERNAME'
- '@@SERVERNAME_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- '@@SERVERNAME function'
- local servers [SQL Server]
ms.assetid: b0ef33fb-954a-4294-b05b-a87c14ce25a3
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5f1e7dbd47562368653ce75eee9d2a412164a9c9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40servername-transact-sql"></a>&#x40;&#x40;SERVERNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il nome del server locale che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
@@SERVERNAME  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar**  
  
## <a name="remarks"></a>Osservazioni  
 Durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il nome del server viene impostato sul nome del computer. Per modificare il nome del server, utilizzare **sp_addserver**, quindi riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Con più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installato, @@SERVERNAME restituisce informazioni sul nome del server locale seguente se il nome del server locale non è stato modificato dopo l'installazione.  
  
|Istanza|Informazioni sul server|  
|--------------|------------------------|  
|Istanza predefinita|'*servername*'|  
|Istanza denominata|'*servername*\\*instancename*'|  
|Istanza cluster di failover, istanza predefinita|'*virtualservername*'|  
|Istanza cluster di failover, istanza denominata|'*virtualservername*\\*instancename*'|  
  
 Sebbene il @@SERVERNAME (funzione) e la proprietà SERVERNAME della funzione SERVERPROPERTY possono restituire stringhe con formati simili, le informazioni possono essere diversi. Nella proprietà SERVERNAME vengono riportate automaticamente le modifiche al nome di rete del computer.  
  
 Al contrario, @@SERVERNAME non riporta tali modifiche. @@SERVERNAME segnala le modifiche apportate al nome di server locale utilizzando il **sp_addserver** o **sp_dropserver** stored procedure.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di `@@SERVERNAME`.  
  
```  
SELECT @@SERVERNAME AS 'Server Name'  
```  
  
 Set di risultati di esempio:  
  
```  
Server Name  
---------------------------------  
ACCTG  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di configurazione &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sp_addserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)  
  
  
