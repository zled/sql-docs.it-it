---
title: DROP EVENT SESSION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_EVENT_SESSION_TSQL
- DROP EVENT SESSION
dev_langs:
- TSQL
helpviewer_keywords:
- event sessions [SQL Server]
- DROP EVENT SESSION statement
ms.assetid: 92eabe4b-24e2-43b1-978c-31a199964b90
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 2d0bca5ece051f8c208c9985e1601c5491e4413b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692899"
---
# <a name="drop-event-session-transact-sql"></a>DROP EVENT SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di eliminare una sessione eventi.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP EVENT SESSION event_session_name  
ON SERVER  
```  
  
## <a name="arguments"></a>Argomenti  
 *event_session_name*  
 Nome di una sessione dell'evento esistente.  
  
## <a name="remarks"></a>Remarks  
 Quando si rilascia una sessione dell'evento, ogni informazioni di configurazione, ad esempio parametri delle destinazioni e della sessione, viene rimossa completamente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER ANY EVENT SESSION.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come eliminare una sessione dell'evento.  
  
```  
DROP EVENT SESSION evt_spin_lock_diagnosis  
ON SERVER;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/create-event-session-transact-sql.md)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [sys.server_event_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)  
  
  
