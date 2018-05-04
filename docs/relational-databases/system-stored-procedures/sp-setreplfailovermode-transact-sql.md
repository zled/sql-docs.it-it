---
title: sp_setreplfailovermode (Transact-SQL) | Documenti Microsoft
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
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 876394cf1f70aec14898a329d24504b1dc1f5878
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spsetreplfailovermode-transact-sql"></a>sp_setreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di impostare la modalità di failover per le sottoscrizioni abilitate per l'aggiornamento immediato sostituito dall'aggiornamento in coda in caso di errore. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore. Per ulteriori informazioni sulle modalità di failover, vedere [sottoscrizioni aggiornabili per la replica transazionale](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_setreplfailovermode [ @publisher= ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication= ] 'publication' ]  
    [ , [ @failover_mode= ] 'failover_mode' ]  
    [ , [ @override = ] override ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher=**] **'***publisher***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito. È necessario che la pubblicazione esista già.  
  
 [  **@publisher_db =**] **'***publisher_db***'**  
 Nome del database di pubblicazione. *publisher_db* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione*viene **sysname**, non prevede alcun valore predefinito.  
  
 [**@failover_mode=**] **'***failover_mode***'**  
 Modalità di failover per la sottoscrizione. *failover_mode* viene **nvarchar(10)** e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**controllo immediato** o **sincronizzazione**|Per le modifiche apportate ai dati nel Sottoscrittore viene eseguita la copia bulk nel server di pubblicazione a mano a mano che vengono implementate.|  
|**In coda**|Le modifiche dei dati vengono archiviate in un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coda.|  
  
> [!NOTE]  
>  L'utilizzo di MSMQ ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing) è deprecato e non è più supportato.  
  
 [ **@override**=] *eseguire l'override*  
 Solo per uso interno.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_setreplfailovermode** consente la replica snapshot o transazionale per le sottoscrizioni sono abilitate, sia per l'aggiornamento con il failover all'aggiornamento immediato in coda o per l'aggiornamento immediato con failover in coda l'aggiornamento.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_setreplfailovermode**.  
  
## <a name="see-also"></a>Vedere anche  
 [Passare alla modalità di aggiornamento per una sottoscrizione transazionale aggiornabile](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
