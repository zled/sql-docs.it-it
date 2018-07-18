---
title: sysmail_help_queue_sp (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysmail_help_queue_sp
- sysmail_help_queue_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_queue_sp
ms.assetid: 94840482-112c-4654-b480-9b456c4c2bca
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3b5087f212e72f4fa6970aff614983d8116d1f5b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33259521"
---
# <a name="sysmailhelpqueuesp-transact-sql"></a>sysmail_help_queue_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In Posta elettronica database esistono due code, la coda della posta e la coda dello stato. Nella coda della posta vengono archiviati gli elementi di posta in attesa di essere inviati. Nella coda dello stato viene archiviato lo stato degli elementi già inviati. Questa stored procedure consente di visualizzare lo stato della coda della posta o dello stato. Se il parametro **@queue_type** non viene specificato, la stored procedure restituisce una riga per ognuna delle code.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_help_queue_sp  [ @queue_type = ] 'queue_type'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@queue_type** =] **'***queue_type***'**  
 Messaggi di posta elettronica del tipo specificato come argomento facoltativo che elimina il *queue_type*. *queue_type* viene **nvarchar(6)** non prevede alcun valore predefinito. Le voci valide sono **posta** e **stato**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-set"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**queue_type**|**nvarchar(6)**|Tipo di coda. I valori possibili sono **posta** e **stato**.|  
|**lunghezza**|**int**|Numero di elementi di posta nella coda specificata.|  
|**state**|**nvarchar(64)**|Stato del server di monitoraggio. I valori possibili sono **inattivo** (coda è inattiva), **NOTIFIED** (coda ha ricevuto una notifica di), e **RECEIVES_OCCURRING** (coda riceve).|  
|**last_empty_rowset_time**|**DATA/ORA**|Data e ora dell'ultimo svuotamento della coda, sia nel formato 24 ore sia nel fuso orario GMT.|  
|**last_activated_time**|**DATA/ORA**|Data e ora dell'ultima attivazione della coda, sia nel formato 24 ore sia nel fuso orario GMT.|  
  
## <a name="remarks"></a>Osservazioni  
 Quando la risoluzione dei problemi di posta elettronica Database, utilizzare **sysmail_help_queue_sp** per visualizzare il numero di elementi presenti nella coda, lo stato della coda e l'ultima attivazione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, solo i membri del **sysadmin** ruolo predefinito del server può accedere a questa procedura.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite entrambe le code della posta e dello stato.  
  
```  
EXECUTE msdb.dbo.sysmail_help_queue_sp ;  
GO  
```  
  
 Set di risultati di esempio, modificato per motivi di lunghezza.  
  
```  
queue_type length      state              last_empty_rowset_time  last_activated_time  
---------- -------- ------------------ ----------------------- -----------------------  
mail       0        RECEIVES_OCCURRING 2005-10-07 21:14:47.010 2005-10-10 20:52:51.517  
status     0        INACTIVE           2005-10-07 21:04:47.003 2005-10-10 21:04:47.003  
  
(2 row(s) affected)  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)  
  
  
