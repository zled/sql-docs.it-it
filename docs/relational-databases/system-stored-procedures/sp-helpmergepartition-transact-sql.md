---
title: sp_helpmergepartition (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- sp_helpmergepartition
- sp_helpmergepartition_TSQL
helpviewer_keywords: sp_helpmergepartition
ms.assetid: 184188cc-f519-445d-97ce-aae38f1eb550
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a2c4e931f2da9794392056595ab71b88e005a26f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpmergepartition-transact-sql"></a>sp_helpmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulla partizione per la pubblicazione di tipo merge specificata. Questa stored procedure viene eseguita in qualsiasi database del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpmergepartition [ @publication= ] 'publication'   
    [ , [ @suser_sname = ] 'suser_sname' ]  
    [ , [ @host_name = ] 'host_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@suser_sname=** ] **'***suser_sname***'**  
 Valore SUSER_SNAME utilizzato per definire una partizione. *SUSER_SNAME* è **sysname**, con un valore predefinito null. Specificare questo parametro per limitare il set di risultati alle partizioni in cui SUSER_SNAME corrisponde al valore specificato.  
  
> [!NOTE]  
>  Quando *suser_sname* viene fornito, *host_name* deve essere NULL  
  
 [  **@host_name=** ] **'***host_name***'**  
 Valore HOST_NAME utilizzato per definire una partizione. *HOST_NAME* è **sysname**, con un valore predefinito null. Specificare questo parametro per limitare il set di risultati alle partizioni in cui HOST_NAME corrisponde al valore specificato.  
  
> [!NOTE]  
>  Quando *suser_sname* viene fornito, *host_name* deve essere NULL  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**partizione**|**int**|Identifica la partizione del Sottoscrittore.|  
|**HOST_NAME**|**sysname**|Valore utilizzato durante la creazione della partizione per una sottoscrizione filtrata in base al valore della [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) funzione nel Sottoscrittore.|  
|**SUSER_SNAME**|**sysname**|Valore utilizzato durante la creazione della partizione per una sottoscrizione filtrata in base al valore della [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) funzione nel Sottoscrittore.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Percorso dello snapshot dei dati filtrati per la partizione del Sottoscrittore.|  
|**date_refreshed**|**datetime**|Data dell'ultima esecuzione del processo snapshot per generare lo snapshot dei dati filtrati per la partizione.|  
|**dynamic_snapshot_jobid**|**uniqueidentifier**|Identifica il processo per la creazione dello snapshot dei dati filtri per una partizione.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpmergepartition** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server e **db_owner** ruolo predefinito del database possono eseguire **sp_helpmergepartition**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addmergepartition &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_dropmergepartition &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropmergepartition-transact-sql.md)  
  
  
