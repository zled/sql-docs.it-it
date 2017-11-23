---
title: sp_configure_peerconflictdetection (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_configure_peerconflictdetection_TSQL
- sp_configure_peerconflictdetection
helpviewer_keywords: sp_configure_peerconflictdetection
ms.assetid: 45117cb2-3247-433f-ba3d-7fa19514b1c3
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f1fed4cb47795554df26deb08f496edba86b5a4d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spconfigurepeerconflictdetection-transact-sql"></a>sp_configure_peerconflictdetection (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Configura il rilevamento dei conflitti per una pubblicazione coinvolta in una topologia di replica transazionale peer-to-peer. Per altre informazioni, vedere [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md). Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_configure_peerconflictdetection [ @publication = ] 'publication'  
    [ , [ @action = ] 'action']  
    [ , [ @originator_id = ] originator_id ]  
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @continue_onconflict = ] 'continue_onconflict']  
    [ , [ @local = ] 'local']  
    [ , [ @timeout = ] timeout ]  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @publication=] '*pubblicazione*'  
 Nome della pubblicazione per cui si desidera configurare il rilevamento dei conflitti. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [ @action=] '*azione*'  
 Specifica se abilitare o disabilitare il rilevamento dei conflitti per una pubblicazione. *azione* è **nvarchar (5)**, e può essere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**abilitare**|Abilita il rilevamento dei conflitti per una pubblicazione.|  
|**disabilitare**|Disabilita il rilevamento dei conflitti per una pubblicazione.|  
|NULL (predefinito)||  
  
 [ @originator_id=] *originator_id*  
 Specifica un ID per un nodo in una topologia peer-to-peer. *originator_id* è **int**, con un valore predefinito è NULL. Questo ID viene utilizzato per il rilevamento dei conflitti se *azione* è impostato su **abilitare**. Specificare un ID positivo diverso da zero che non sia mai stato utilizzato nella topologia. Per un elenco degli ID che sono già stati utilizzati, eseguire una query sulla tabella di sistema [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) .  
  
 [ @conflict_retention=] *conflict_retention*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @continue_onconflict=] '*continue_onconflict*']  
 Determina se l'agente di distribuzione continua a elaborare le modifiche dopo che è stato rilevato un conflitto. *continue_onconflict* è **nvarchar (5)** con valore predefinito è false.  
  
> [!CAUTION]  
>  È consigliabile utilizzare il valore predefinito FALSE. Quando questa opzione è impostata su TRUE, l'agente di distribuzione tenta di garantire la convergenza dei dati nella topologia applicando la riga in conflitto dal nodo con ID di origine maggiore. Questo metodo non garantisce la convergenza. Dopo il rilevamento di un conflitto, è necessario assicurarsi che la topologia sia coerente. Per ulteriori informazioni, vedere la sezione relativa alla gestione dei conflitti in [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
 [ @local=] '*locale*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @timeout=] *timeout*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 sp_configure_peerconflictdetection è utilizzato nella replica transazionale peer-to-peer. Per utilizzare il rilevamento dei conflitti, è necessario eseguire tutti i nodi [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] o versioni successive versioni; e il rilevamento deve essere abilitato per tutti i nodi.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo predefinito del server sysadmin o al ruolo predefinito del database db_owner.  
  
## <a name="see-also"></a>Vedere anche  
 [Peer-to-peer - Rilevamento dei conflitti nella replica](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)   
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
