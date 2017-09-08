---
title: '@@CONNECTIONS (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@CONNECTIONS'
- '@@CONNECTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CONNECTIONS function'
- connections [SQL Server], number of
- connections [SQL Server], attempted
- number of connection attempts
- attempted connections
ms.assetid: c59836a8-443c-4b9a-8b96-8863ada97ac7
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5619f7fd0ea769af7a614178be5242174cc66fde
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="connections-transact-sql"></a>@@CONNECTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
@@MAX_CONNECTIONS è il numero massimo di connessioni simultanee consentite al server. @@CONNECTIONS viene incrementato ad ogni tentativo di accesso, pertanto@CONNECTIONS può essere maggiore di @@MAX_CONNECTIONS.
  
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
[Funzioni statistiche di sistema &#40; Transact-SQL &#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
[la procedura sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)
  
  

