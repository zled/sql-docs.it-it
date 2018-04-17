---
title: sp_replmonitorsubscriptionpendingcmds (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- sp_replmonitorsubscriptionpendingcmds_TSQL
- sp_replmonitorsubscriptionpendingcmds
helpviewer_keywords:
- sp_replmonitorsubscriptionpendingcmds
ms.assetid: df5b955a-feb0-4863-9b3b-7f71e9653b3d
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4b4ff275583ac65fe3588e5fd0c0f41931da74f0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spreplmonitorsubscriptionpendingcmds-transact-sql"></a>sp_replmonitorsubscriptionpendingcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sul numero di comandi in sospeso per una sottoscrizione di una pubblicazione transazionale e una stima approssimativa del tempo necessario per l'elaborazione di tali comandi. Questa stored procedure restituisce una riga per ogni sottoscrizione restituita. Questa stored procedure, utilizzata per il monitoraggio della replica, viene eseguita nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replmonitorsubscriptionpendingcmds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @subscription_type = ] subscription_type  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@publisher_db** = ] **'***publisher_db***'**  
 Nome del database pubblicato. *publisher_db* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@publication** =] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@subscriber** =] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@subscriber_db** = ] **'***subscriber_db***'**  
 Nome del database di sottoscrizione. *subscriber_db* viene **sysname**, non prevede alcun valore predefinito.  
  
 [ **@subscription_type** =] *subscription_type*  
 Tipo di sottoscrizione: *publication_type* viene **int**e non prevede alcun valore predefinito e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**0**|Sottoscrizione push|  
|**1**|Sottoscrizione pull|  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**pendingcmdcount**|**int**|Numero di comandi in sospeso per la sottoscrizione.|  
|**estimatedprocesstime**|**int**|Stima del numero di secondi necessari per il recapito di tutti i comandi in sospeso al Sottoscrittore.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replmonitorsubscriptionpendingcmds** viene utilizzato con la replica transazionale.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** al server di distribuzione o i membri del ruolo predefinito del server di **db_owner** ruolo predefinito del database nel database di distribuzione possono eseguire **sp _ replmonitorsubscriptionpendingcmds**. Elenco dei membri dell'accesso alla pubblicazione per una pubblicazione che utilizza il database di distribuzione può eseguire **sp_replmonitorsubscriptionpendingcmds** per restituire i comandi in sospeso per tale pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare la replica a livello di programmazione](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
