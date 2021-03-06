---
title: sp_setreplfailovermode (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_setreplfailovermode
- sp_setreplfailovermode_TSQL
helpviewer_keywords:
- sp_setreplfailovermode
ms.assetid: ca98a4c3-bea4-4130-88d7-79e0fd1e85f6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 97254571aaa19acb71928424a20ec9ffb741ee02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772939"
---
# <a name="spsetreplfailovermode-transact-sql"></a>sp_setreplfailovermode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di impostare la modalità di failover per le sottoscrizioni abilitate per l'aggiornamento immediato sostituito dall'aggiornamento in coda in caso di errore. Questa stored procedure viene eseguita nel database di sottoscrizione del Sottoscrittore. Per altre informazioni sulle modalità di failover, vedere [le sottoscrizioni aggiornabili per la replica transazionale](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
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
 Modalità di failover per la sottoscrizione. *failover_mode* viene **nvarchar(10)** i possibili valori sono i seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|**controllo immediato** o **sincronizzazione**|Per le modifiche apportate ai dati nel Sottoscrittore viene eseguita la copia bulk nel server di pubblicazione a mano a mano che vengono implementate.|  
|**In coda**|Le modifiche dei dati vengono archiviate in un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] coda.|  
  
> [!NOTE]  
>  L'utilizzo di MSMQ ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing) è deprecato e non è più supportato.  
  
 [ **@override**=] *eseguire l'override*  
 Solo per uso interno.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_setreplfailovermode** consente la replica snapshot o transazionale per le sottoscrizioni sono abilitate, sia per l'aggiornamento con failover all'aggiornamento immediato in coda o per l'aggiornamento immediato con failover in coda l'aggiornamento.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server oppure **db_owner** ruolo predefinito del database possono eseguire **sp_setreplfailovermode**.  
  
## <a name="see-also"></a>Vedere anche  
 [Alternare le modalità di aggiornamento per una sottoscrizione transazionale aggiornabile](../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
