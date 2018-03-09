---
title: sp_check_subset_filter (Transact-SQL) | Documenti Microsoft
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
- sp_check_TSQL
- sp_check_subset_filter
- filter
- subset
- subset_TSQL
- sp_check
- sp_check_subset_filter_TSQL
helpviewer_keywords:
- sp_check_subset_filter
ms.assetid: 525cfcfc-f317-478d-ba84-72e62285f160
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3341c4f5fc6c637f74dabf913730e6c6e30dfcea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spchecksubsetfilter-transact-sql"></a>sp_check_subset_filter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa stored procedure viene utilizzata per controllare una clausola di filtro in qualsiasi tabella per determinarne la validità per la tabella e per restituire informazioni sul filtro specificato, incluso se il filtro può essere utilizzato con partizioni pre-calcolate. Questa stored procedure viene eseguita nel database contenente la pubblicazione nel server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_check_subset_filter [ @filtered_table = ] 'filtered_table'  
        , [ @subset_filterclause = ] 'subset_filterclause'  
    [ , [ @has_dynamic_filters = ] has_dynamic_filters OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@filtered_table** =] **'***filtered_table***'**  
 Nome della tabella filtrata. *filtered_table* è **nvarchar (400)**, non prevede alcun valore predefinito.  
  
 [  **@subset_filterclause**  =] **'***subset_filterclause***'**  
 Clausola di filtro sottoposta a verifica. *subset_filterclause* è **nvarchar (1000)**, non prevede alcun valore predefinito.  
  
 [  **@has_dynamic_filters** =] *has_dynamic_filters*  
 Indica se la clausola di filtro è un filtro di riga con parametri. *has_dynamic_filters* è **bit**, con un valore predefinito è NULL ed è un parametro di output. Restituisce un valore di **1** quando la clausola di filtro è un filtro di riga con parametri.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|Specifica se la pubblicazione consente l'utilizzo di partizioni pre-calcolate; dove **1** significa che le partizioni calcolate possono essere utilizzate, e **0** significa che non possono essere utilizzate.|  
|**has_dynamic_filters**|**bit**|Specifica se la clausola di filtro include almeno un filtro di riga con parametri. dove **1** significa che viene utilizzato un filtro di riga con parametri, e **0** significa che tale funzione non è stata utilizzata.|  
|**dynamic_filters_function_list**|**nvarchar (500)**|Elenca le funzioni nella clausola di filtro che filtrano dinamicamente un articolo. Ogni funzione è separata da un punto e virgola.|  
|**uses_host_name**|**bit**|Se il [HOST_NAME ()](../../t-sql/functions/host-name-transact-sql.md) funzione viene utilizzata nella clausola di filtro, in cui **1** significa che questa funzione è presenta.|  
|**uses_suser_sname**|**bit**|Se il [SUSER_SNAME ()](../../t-sql/functions/suser-sname-transact-sql.md) funzione viene utilizzata nella clausola di filtro, in cui **1** significa che questa funzione è presenta.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_check_subset_filter** viene utilizzata nella replica di tipo merge.  
  
 **sp_check_subset_filter** può essere eseguito su qualsiasi tabella anche se la tabella non è pubblicata. Questa stored procedure può essere utilizzata per verificare una clausola di filtro prima di definire un articolo filtrato.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_check_subset_filter**.  
  
## <a name="see-also"></a>Vedere anche  
 [Ottimizzare le prestazioni di filtro con parametri con partizioni pre-calcolate](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)  
  
  
