---
title: sp_replqueuemonitor (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sp_replqueuemonitor
- sp_replqueuemonitor_TSQL
helpviewer_keywords:
- sp_replqueuemonitor
ms.assetid: 6909a3f1-43a2-4df5-a6a5-9e6f347ac841
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 37da715db8fbdd39c768ef95bf541526a9ab0942
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spreplqueuemonitor-transact-sql"></a>sp_replqueuemonitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elenca i messaggi in coda da un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coda o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Accodamento messaggi per le sottoscrizioni ad aggiornamento in coda per una pubblicazione specificata. Se si utilizzano code di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore. In caso di utilizzo di Message Queuing, la stored procedure viene eseguita nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replqueuemonitor [ @publisher = ] 'publisher'  
    [ , [ @publisherdb = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @tranid = ] 'tranid' ]  
    [ , [ @queuetype = ] 'queuetype' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@publisher** =] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* viene **sysname**, con un valore predefinito è NULL. Il server deve essere configurato per la pubblicazione. Il valore NULL indica tutti i server di pubblicazione.  
  
 [ **@publisherdb** =] **'***publisher_db***'** ]  
 Nome del database di pubblicazione. *publisher_db* viene **sysname**, con un valore predefinito è NULL. che indica tutti i database di pubblicazione.  
  
 [ **@publication** =] **'***pubblicazione***'** ]  
 Nome della pubblicazione. *pubblicazione*viene **sysname**, con un valore predefinito è NULL. che indica tutte le pubblicazioni.  
  
 [ **@tranid** =] **'***tranid***'** ]  
 ID transazione. *tranid*viene **sysname**, con un valore predefinito è NULL. che indica tutte le transazioni.  
  
 [**@queuetype=** ] **'***queuetype***'** ]  
 Tipo di coda in cui vengono archiviate le transazioni. *queuetype* viene **tinyint** con valore predefinito è **0**, e può essere uno dei valori seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**0**|Tutti i tipi di coda|  
|**1**|accodamento messaggi|  
|**2**|Coda di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replqueuemonitor** viene utilizzata per la replica snapshot o transazionale con sottoscrizioni ad aggiornamento in coda. I messaggi in coda che non includono comandi SQL o che fanno parte di un comando SQL esteso non vengono visualizzati.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_replqueuemonitor**.  
  
## <a name="see-also"></a>Vedere anche  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
