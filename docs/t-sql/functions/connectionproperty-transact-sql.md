---
title: CONNECTIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONNECTIONPROPERTY_TSQL
- CONNECTIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- CONNECTIONPROPERTY statement
ms.assetid: 6bd9ccae-af77-4a05-b97f-f8ab41cfde42
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ab513c11d86ca5d7496ad1fca2ff7527d69bba6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="connectionproperty-transact-sql"></a>CONNECTIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce informazioni sulle proprietà di connessione per la connessione univoca da cui si è ricevuta la richiesta.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CONNECTIONPROPERTY ( property )  
```  
  
## <a name="arguments"></a>Argomenti  
*property*  
Proprietà della connessione. I possibili valori di *property* sono i seguenti.
  
|valore|Tipo di dati|Description|  
|---|---|---|
|net_transport|**nvarchar(40)**|Restituisce il protocollo di trasporto fisico utilizzato dalla connessione. Non ammette i valori Null.<br /><br /> I valori restituiti sono: **HTTP**, **Named pipe**, **Session**, **Shared memory**, **SSL**, **TCP** e **VIA**.<br /><br /> Nota: viene restituito sempre **Session** quando per una connessione è abilitata la funzionalità MARS (Multiple Active Result Set) e il pool di connessioni.|  
|protocol_type|**nvarchar(40)**|Restituisce il tipo di protocollo del payload. Attualmente distingue tra TDS (TSQL) e SOAP. Ammette i valori Null.|  
|auth_scheme|**nvarchar(40)**|Restituisce lo schema di autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per una connessione. Lo schema di autenticazione può essere relativo all'autenticazione di Windows (NTLM, KERBEROS, DIGEST, BASIC, NEGOTIATE) o all'autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non ammette i valori Null.|  
|local_net_address|**varchar(48)**|Restituisce l'indirizzo IP del server di destinazione della connessione. Disponibile solo per le connessioni che utilizzano il provider del trasporto TCP. Ammette i valori Null.|  
|local_tcp_port|**int**|Restituisce la porta TCP del server che verrebbe impiegata nel caso in cui la connessione utilizzasse il trasporto TCP. Ammette i valori Null.|  
|client_net_address|**varchar(48)**|Richiede l'indirizzo host del client che si connette al server. Ammette i valori Null.|  
|physical_net_transport|**nvarchar(40)**|Restituisce il protocollo di trasporto fisico utilizzato dalla connessione. È accurato quando per una connessione è abilitata la funzionalità MARS (Multiple Active Result Set).|  
|\<Qualsiasi altra stringa>||Restituisce NULL se l'input non è valido.|  
  
## <a name="remarks"></a>Remarks  
**local_net_address** e **local_tcp_port** restituiscono NULL in [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
I valori restituiti corrispondono alle opzioni mostrate per le colonne corrispondenti nella DMV [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md). Ad esempio
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>Vedere anche
[sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  
