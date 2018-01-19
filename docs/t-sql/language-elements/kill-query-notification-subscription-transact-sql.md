---
title: KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION
- KILL_QUERY_NOTIFICATION_SUBSCRIPTION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- KILL QUERY NOTIFICATION SUBSCRIPTION statement
- removing subscriptions
- subscriptions [SQL Server query notifications], stopping
- query notifications [SQL Server], subscriptions
ms.assetid: 8aeadf51-286c-4748-bef2-d25858b250bf
caps.latest.revision: "17"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e9c1a2a3af3ce113573fe743aa2325ae0b49cc18
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="kill-query-notification-subscription-transact-sql"></a>KILL QUERY NOTIFICATION SUBSCRIPTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove le sottoscrizioni di notifica delle query dall'istanza. Questa istruzione può rimuovere una sottoscrizione specifica oppure tutte le sottoscrizioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
KILL QUERY NOTIFICATION SUBSCRIPTION   
   { ALL | subscription_id }  
```  
  
## <a name="arguments"></a>Argomenti  
 ALL  
 Rimuove tutte le sottoscrizioni nell'istanza.  
  
 *subscription_id*  
 Rimuove la sottoscrizione con l'id sottoscrizione *subscription_id*.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione KILL QUERY NOTIFICATION SUBSCRIPTION rimuove le sottoscrizioni di notifica delle query senza generare un messaggio di notifica.  
  
 *subscription_id* è l'id per la sottoscrizione, come illustrato nella vista a gestione dinamica [Sys.dm qn_subscriptions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md).  
  
 Se l'ID sottoscrizione specificato non esiste, l'istruzione genera un errore.  
  
## <a name="permissions"></a>Autorizzazioni  
 Autorizzazione per eseguire questa istruzione è limitato ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-removing-all-query-notification-subscriptions-in-the-instance"></a>A. Rimozione di tutte le sottoscrizioni di notifica delle query nell'istanza  
 Nell'esempio seguente vengono rimosse tutte le sottoscrizioni di notifica delle query nell'istanza.  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION ALL ;  
```  
  
### <a name="b-removing-a-single-query-notification-subscription"></a>B. Rimozione di una sottoscrizione di notifica delle query  
 Nell'esempio seguente viene rimossa la sottoscrizione di notifica delle query associata all'ID `73`.  
  
```  
KILL QUERY NOTIFICATION SUBSCRIPTION 73 ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_qn_subscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/query-notifications-sys-dm-qn-subscriptions.md)  
  
  
