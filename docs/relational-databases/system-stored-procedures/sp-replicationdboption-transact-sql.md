---
title: sp_replicationdboption (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_replicationdboption_TSQL
- sp_replicationdboption
helpviewer_keywords:
- sp_replicationdboption
ms.assetid: d021864e-3f21-4d1a-89df-6c1086f753bf
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9a88d295f6ae5ff0fcfab7121a4057dd84f75957
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33000328"
---
# <a name="spreplicationdboption-transact-sql"></a>sp_replicationdboption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta un'opzione del database di replica per il database specificato. Questa stored procedure viene eseguita in qualsiasi database del server di pubblicazione o del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replicationdboption [ @dbname= ] 'db_name'   
        , [ @optname= ] 'optname'   
        , [ @value= ] 'value'   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
    [ , [ @from_scripting = ] from_scripting ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [**@dbname=**] **'***dbname***'**  
 Database per cui si desidera impostare l'opzione del database di replica. *db_name* viene **sysname**, non prevede alcun valore predefinito.  
  
 [**@optname=**] **'***optname***'**  
 Opzione del database di replica che si desidera abilitare o disabilitare. *optname* viene **sysname**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**pubblicazione di tipo merge**|Specifica se il database può essere utilizzato per pubblicazioni di tipo merge.|  
|**Pubblicazione**|Specifica se il database può essere utilizzato per altri tipi di pubblicazione.|  
|**La sottoscrizione**|Specifica se si tratta di un database di sottoscrizione.|  
|**la sincronizzazione con backup**|Specifica se il database è abilitato per il backup coordinato. Per altre informazioni, vedere [abilitare i backup coordinati per la replica transazionale &#40;programmazione Transact-SQL della replica&#41;](../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md).|  
  
 [  **@value=**] **'***valore***'**  
 Specifica se l'opzione del database di replica deve essere abilitata o disabilitata. *valore* viene **sysname**e può essere **true** oppure **false**. Quando questo valore è **false** e *optname* è **la pubblicazione di tipo merge**, vengono eliminate anche le sottoscrizioni di database di pubblicazione di tipo merge.  
  
 [  **@ignore_distributor=**] *ignore_distributor*  
 Indica se questa stored procedure viene eseguita senza stabilire la connessione al server di distribuzione. *ignore_distributor* viene **bit**, il valore predefinito è **0**, vale a dire il server di distribuzione deve essere connesso a e aggiornato con il nuovo stato del database di pubblicazione. Il valore **1** deve essere specificato solo se il server di distribuzione non è accessibile e **sp_replicationdboption** viene utilizzata per disabilitare la pubblicazione.  
  
 [  **@from_scripting=**] *from_scripting*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replicationdboption** viene utilizzata nella replica snapshot, transazionale e di tipo merge.  
  
 Questa procedura crea o elimina tabelle del sistema di replica specifiche, account di sicurezza specifici e così via a seconda delle opzioni impostate. Imposta la categoria corrispondente bit nel **sysdatabases** tabella di sistema e crea le tabelle di sistema necessarie.  
  
 Per disabilitare la pubblicazione, è necessario che il database di pubblicazione sia online. Se esiste uno snapshot per il database di pubblicazione, deve essere eliminato prima della disabilitazione della pubblicazione. Uno snapshot del database è una copia offline e di sola lettura di un database e non è correlato a uno snapshot di replica. Per altre informazioni, vedere [Snapshot del database &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_replicationdboption**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la pubblicazione e la distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Creare una pubblicazione](../../relational-databases/replication/publish/create-a-publication.md)   
 [Eliminazione di una pubblicazione](../../relational-databases/replication/publish/delete-a-publication.md)   
 [Disabilitare la pubblicazione e la distribuzione](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [Sys. sysdatabases &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)   
 [Stored procedure per la replica &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
