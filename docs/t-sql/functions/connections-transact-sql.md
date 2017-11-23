---
title: '@@CONNECTIONS (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@CONNECTIONS'
- '@@CONNECTIONS_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- '@@CONNECTIONS function'
- connections [SQL Server], number of
- connections [SQL Server], attempted
- number of connection attempts
- attempted connections
ms.assetid: c59836a8-443c-4b9a-8b96-8863ada97ac7
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8422da0d4e550c99fac6c9659f771ab98196cb4a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40connections-transact-sql"></a>&#x40;&#x40;CONNESSIONI (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Restituisce il numero di tentativi di connessione, con esito positivo o negativo, dopo l'ultimo avvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
@@CONNECTIONS  
```  
  
## <a name="return-types"></a>Tipi restituiti
**integer**
  
## <a name="remarks"></a>Osservazioni  
Le connessioni sono distinte dagli utenti. Nelle applicazioni, ad esempio, è possibile aprire più connessioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza che siano visibili all'utente.
  
Per visualizzare un report contenente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] statistiche, tra cui i tentativi di connessione, eseguire **sp_monitor**.
  
@@MAX_CONNECTIONS è il numero massimo di connessioni simultanee consentite al server. @@CONNECTIONS viene incrementato ad ogni tentativo di accesso, pertanto @@CONNECTIONS può essere maggiore di @@MAX_CONNECTIONS .
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente viene illustrato il numero di tentativi di accesso in corrispondenza della data e dell'ora correnti.
  
```sql
SELECT GETDATE() AS 'Today''s Date and Time',   
@@CONNECTIONS AS 'Login Attempts';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
  
Today's Date and Time  Login Attempts  
---------------------- --------------  
12/5/2006 10:32:45 AM  211023         
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni statistiche di sistema &#40;Transact-SQL&#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
[la procedura sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)
  
  
