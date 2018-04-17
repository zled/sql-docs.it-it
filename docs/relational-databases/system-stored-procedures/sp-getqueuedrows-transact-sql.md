---
title: sp_getqueuedrows (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_getqueuedrows_TSQL
- sp_getqueuedrows
helpviewer_keywords:
- sp_getqueuedrows
ms.assetid: 139e834f-1988-4b4d-ac81-db1f89ea90e8
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1915bec9f0a9f1e05bfe6a2975553bb20e330289
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spgetqueuedrows-transact-sql"></a>sp_getqueuedrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Recupera le righe nel Sottoscrittore per le quali esistono aggiornamenti in sospeso nella coda. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_getqueuedrows [ @tablename = ] 'tablename'  
    [ , [ @owner = ] 'owner'  
    [ , [ @tranid = ] 'transaction_id' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@tablename =**] **'***tablename***'**  
 Nome della tabella. *TableName* viene **sysname**, non prevede alcun valore predefinito. La tabella deve essere inclusa in una sottoscrizione in coda.  
  
 [  **@owner =**] **'***proprietario***'**  
 Proprietario della sottoscrizione. *proprietario* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@tranid =** ] **'***transaction_id***'**  
 Consente il filtraggio dell'output in base all'ID della transazione. *transaction_id* viene **nvarchar(70)**, con un valore predefinito è NULL. Se specificato, viene visualizzato l'ID della transazione associato al comando in coda. Se è NULL, vengono visualizzati tutti i comandi nella coda.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Visualizza tutte le righe alle quali è associata almeno una transazione in coda per la tabella sottoscritta.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**Azione**|**nvarchar(10)**|Tipo di azione da eseguire in corrispondenza della sincronizzazione.<br /><br /> INS= inserimento<br /><br /> DEL = eliminazione<br /><br /> UPD = aggiornamento|  
|**Tranid**|**nvarchar(70)**|ID della transazione in cui è stato eseguito il comando.|  
|**tabella column1... n**||Il valore per ogni colonna della tabella specificata *tablename*.|  
|**MSrepl_tran_version**|**uniqueidentifier**|Questa colonna viene utilizzata per tenere traccia delle modifiche ai dati replicati e per eseguire il rilevamento dei conflitti nel server di pubblicazione. La colonna viene aggiunta alla tabella automaticamente.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_getqueuedrows** viene utilizzata nei Sottoscrittori che partecipano all'aggiornamento in coda.  
  
 **sp_getqueuedrows** trova le righe di una tabella specifica in una sottoscrizione del database che hanno partecipato un aggiornamento in coda, ma attualmente non sono stati risolti dall'agente di lettura coda.  
  
## <a name="permissions"></a>Autorizzazioni  
 **sp_getqueuedrows** richiede le autorizzazioni SELECT sulla tabella specificata nella *tablename*.  
  
## <a name="see-also"></a>Vedere anche  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Rilevamento e risoluzione dei conflitti per l'aggiornamento in coda](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
