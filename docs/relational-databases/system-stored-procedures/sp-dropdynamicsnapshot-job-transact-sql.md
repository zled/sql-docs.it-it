---
title: sp_dropdynamicsnapshot_job (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_dropdynamicsnapshot_job_TSQL
- sp_dropdynamicsnapshot_job
helpviewer_keywords:
- sp_dropdynamicsnapshot_job
ms.assetid: 128e428a-01b3-4062-8c6e-d22d5fa268a9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3cc6dc65589951513a5d05dbfad68cecb8d92745
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spdropdynamicsnapshotjob-transact-sql"></a>sp_dropdynamicsnapshot_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un processo di snapshot dei dati filtrati per una pubblicazione con filtri di riga con parametri. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione. Quando il processo viene eliminato, tutti i dati correlati vengono eliminati dal [MSdynamicsnapshotjobs](../../relational-databases/system-tables/msdynamicsnapshotjobs-transact-sql.md) tabella di sistema.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dropdynamicsnapshot_job [ @publication = ] 'publication'   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]   
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]   
    [ , [ @ignore_distributor =] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione da cui deve essere rimosso il processo di snapshot dei dati filtrati. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@dynamic_snapshot_jobname** =] **'***dynamic_snapshot_jobname***'**  
 Nome del processo di snapshot dei dati filtrati da rimuovere. *dynamic_snapshot_jobname*è di tipo sysname, e se non è fornito le impostazioni predefinite per il processo è associata a *dynamic_snapshot_jobid*.  
  
 [  **@dynamic_snapshot_jobid** =] **'***dynamic_snapshot_jobid***'**  
 Identificatore per il processo di snapshot dei dati filtrati da rimuovere. *dynamic_snapshot_jobid*è **uniqueidentifier**, con valore predefinito è NULL.  
  
> [!IMPORTANT]  
>  Solo *dynamic_snapshot_jobid*o *dynamic_snapshot_jobname* può essere specificato. Se non sono specificati valori per uno *dynamic_snapshot_jobid*o *dynamic_snapshot_jobname*, vengono rimossi tutti i processi di snapshot dinamico per la pubblicazione.  
  
 [  **@ignore_distributor =**] *ignore_distributor*  
 *ignore_distributor* è **bit**, il valore predefinito è **0**. È possibile utilizzare questo parametro per rimuovere un processo di snapshot dinamico senza eseguire operazioni di pulizia dei riferimenti nel server di distribuzione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_dropdynamicsnapshot** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_dropdynamicsnapshot**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_adddynamicsnapshot_job &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-adddynamicsnapshot-job-transact-sql.md)  
  
  
