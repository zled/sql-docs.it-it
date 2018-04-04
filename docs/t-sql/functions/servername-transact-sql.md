---
title: '@@SERVERNAME (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@SERVERNAME'
- '@@SERVERNAME_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@SERVERNAME function'
- local servers [SQL Server]
ms.assetid: b0ef33fb-954a-4294-b05b-a87c14ce25a3
caps.latest.revision: ''
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 40f441998f2f5055bdacb0ac6d796a6d3ad56f68
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="x40x40servername-transact-sql"></a>&#x40;&#x40;SERVERNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il nome del server locale che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

 ![Icona di collegamento a un articolo](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
@@SERVERNAME  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 Durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il nome del server viene impostato sul nome del computer. Per modificare il nome del server, usare **sp_addserver** e quindi riavviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Se sono installate più istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la funzione @@SERVERNAME restituisce le informazioni seguenti relative al nome del server locale se dopo l'installazione tale nome non è stato modificato.  
  
|Istanza|Informazioni sul server|  
|--------------|------------------------|  
|Istanza predefinita|'*servername*'|  
|Istanza denominata|'*servername*\\*instancename*'|  
|Istanza cluster di failover, istanza predefinita|'*virtualservername*'|  
|Istanza cluster di failover, istanza denominata|'*virtualservername*\\*instancename*'|  
  
 La funzione @@SERVERNAME e la proprietà SERVERNAME della funzione SERVERPROPERTY possono restituire stringhe con formati simili, mentre le informazioni possono essere diverse. Nella proprietà SERVERNAME vengono riportate automaticamente le modifiche al nome di rete del computer.  
  
 La funzione @@SERVERNAME invece non riporta tali modifiche. @@SERVERNAME riporta le modifiche al nome di server locale apportate tramite la stored procedure **sp_addserver** o **sp_dropserver**.  
  
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
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)  
  
  
