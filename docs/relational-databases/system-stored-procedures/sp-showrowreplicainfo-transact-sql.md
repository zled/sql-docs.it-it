---
title: sp_showrowreplicainfo (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- sp_showrowreplicainfo_TSQL
- sp_showrowreplicainfo
helpviewer_keywords: sp_showrowreplicainfo
ms.assetid: 6a9dbc1a-e1e1-40c4-97cb-8164a2288f76
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d584c011b61c8b8ad9e3fc55f10a1e7a2512fa97
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spshowrowreplicainfo-transact-sql"></a>sp_showrowreplicainfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Visualizza informazioni su una riga di una tabella utilizzata come articolo in repliche di tipo merge. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_showrowreplicainfo [ [ @ownername = ] 'ownername' ]  
    [ , [ @tablename =] 'tablename' ]   
        , [ @rowguid =] rowguid   
    [ , [ @show = ] 'show' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@ownername** =] **'***ownername***'**  
 Nome del proprietario della tabella. *ownername* è **sysname**, con un valore predefinito è NULL. Questo parametro risulta utile per differenziare le tabelle quando un database contiene più tabelle aventi lo stesso nome ma appartenenti a proprietari diversi.  
  
 [  **@tablename =**] **'***tablename***'**  
 Nome della tabella che include la riga di cui vengono restituite informazioni. *TableName* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@rowguid =**] *rowguid*  
 Identificatore univoco della riga. *ROWGUID* è **uniqueidentifier**, non prevede alcun valore predefinito.  
  
 [  **@show** =] **'***Mostra***'**  
 Determina la quantità di informazioni da restituire nel set di risultati. *Mostra* è **nvarchar (20)** con un valore predefinito è BOTH. Se **riga**, viene restituiti solo informazioni sulla versione di riga. Se **colonne**, viene restituiti solo informazioni sulla versione di colonna. Se **entrambi**, di righe e vengono restituite informazioni di colonna.  
  
## <a name="result-sets-for-row-information"></a>Set di risultati per informazioni sulla riga  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**nome_server**|**sysname**|Nome del server che include il database in cui è stata immessa la voce sulla versione di riga.|  
|**db_name**|**sysname**|Nome del database in cui è stata immessa la voce.|  
|**db_nickname**|**Binary(6)**|Nome alternativo del database in cui è stata immessa la voce.|  
|**version**|**int**|Versione della voce.|  
|**current_state**|**nvarchar(9)**|Restituisce informazioni sullo stato corrente della riga.<br /><br /> **y** -i dati di riga rappresentano lo stato corrente della riga.<br /><br /> **n**-Dati di riga non rappresentano lo stato corrente della riga.<br /><br /> **\<n/a >** : non applicabile.<br /><br /> **\<sconosciuto >** -non è possibile determinare lo stato corrente.|  
|**rowversion_table**|**nchar(17)**|Indica se le versioni di riga vengono archiviate nel [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) tabella o la [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) tabella.|  
|**commento**|**nvarchar(255)**|Informazioni aggiuntive relative alla voce sulla versione di riga. Questo campo è in genere vuoto.|  
  
## <a name="result-sets-for-column-information"></a>Set di risultati per informazioni sulla colonna  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**nome_server**|**sysname**|Nome del server che include il database in cui è stata immessa la voce sulla versione di colonna.|  
|**db_name**|**sysname**|Nome del database in cui è stata immessa la voce.|  
|**db_nickname**|**Binary(6)**|Nome alternativo del database in cui è stata immessa la voce.|  
|**version**|**int**|Versione della voce.|  
|**colname**|**sysname**|Nome della colonna di articolo rappresentata dalla voce sulla versione di colonna.|  
|**commento**|**nvarchar(255)**|Informazioni aggiuntive relative alla voce sulla versione di colonna. Questo campo è in genere vuoto.|  
  
## <a name="result-set-for-both"></a>Set di risultati per informazioni su riga e colonna  
 Se il valore **entrambi** scelto per *Mostra*, viene restituito il set di risultati sia la riga e colonna.  
  
## <a name="remarks"></a>Osservazioni  
 **sp_showrowreplicainfo** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Permissions  
 **sp_showrowreplicainfo** può essere eseguita solo dai membri del **db_owner** ruolo predefinito del database nel database di pubblicazione o dai membri dell'elenco accesso pubblicazione (PAL) nel database di pubblicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Rilevare e risolvere i conflitti di replica di tipo Merge](../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
