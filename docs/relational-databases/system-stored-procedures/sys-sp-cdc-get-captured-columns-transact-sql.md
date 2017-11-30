---
title: Sys. sp_cdc_get_captured_columns (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cdc_get_captured_columns
- sys.sp_cdc_get_captured_columns
- sys.sp_cdc_get_captured_columns_TSQL
- sp_cdc_get_captured_columns_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.sp_cdc_get_captured_columns
- sp_cdc_get_captured_columns
- change data capture [SQL Server], querying metadata
ms.assetid: d9e680be-ab9b-4e0c-b63a-90658f241df8
caps.latest.revision: "30"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e232446f85dabc19856913ebf2e0cc5f886dc8cb
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sysspcdcgetcapturedcolumns-transact-sql"></a>sys.sp_cdc_get_captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le informazioni sui metadati di Change Data Capture per le colonne di origine acquisite registrate dall'istanza di acquisizione specificata. Change Data Capture non è disponibile in tutte le edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_cdc_get_captured_columns   
    [ @capture_instance = ] 'capture_instance'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @capture_instance =] '*capture_instance*'  
 Nome dell'istanza di acquisizione associata a una tabella di origine. *capture_instance* è **sysname** e non può essere NULL.  
  
 Per segnalare le istanze di acquisizione per la tabella, eseguire il [sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md) stored procedure.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|Nome dello schema della tabella di origine.|  
|source_table|**sysname**|Nome della tabella di origine.|  
|capture_instance|**sysname**|Nome dell'istanza di acquisizione.|  
|column_name|**sysname**|Nome della colonna di origine acquisita.|  
|column_id|**int**|ID della colonna della tabella di origine.|  
|ordinal_position|**int**|Posizione della colonna all'interno della tabella di origine.|  
|data_type|**sysname**|Tipo di dati della colonna.|  
|character_maximum_length|**int**|Lunghezza massima in caratteri della colonna se questa è basata su caratteri. In caso contrario il valore è NULL.|  
|numeric_precision|**tinyint**|Precisione della colonna se questa è basata su valori numerici. In caso contrario il valore è NULL.|  
|numeric_precision_radix|**smallint**|Radice di precisione della colonna se questa è basata su valori numerici. In caso contrario il valore è NULL.|  
|numeric_scale|**int**|Scala della colonna se questa è basata su valori numerici. In caso contrario il valore è NULL.|  
|datetime_precision|**smallint**|Precisione della colonna se questa è basata su valori datetime. In caso contrario il valore è NULL.|  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare Sys. sp_cdc_get_captured_columns per ottenere informazioni sulle colonne acquisite restituite da funzioni di query di istanza di acquisizione query [CDC. fn_cdc_get_all_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md) o [CDC. fn_cdc_get_net_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md). I nomi di colonna, gli ID e la posizione rimangono costanti per tutta la durata dell'istanza di acquisizione. Solo il tipo di dati delle colonne cambia quando cambia il tipo di dati delle colonne di origine sottostanti nella tabella registrata. Le colonne che vengono aggiunti o eliminate da una tabella di origine avere alcun impatto sulle colonne acquisite di istanze di acquisizione esistente.  
  
 Utilizzare [sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md) per ottenere informazioni sulla definizione dei dati (istruzioni DDL language) applicate a una tabella di origine. Le modifiche DDL che influiscono sulla struttura di una colonna di origine registrata vengono restituite nel set di risultati.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'appartenenza al ruolo predefinito del database db_owner. Per tutti gli altri utenti, è richiesta l'autorizzazione SELECT su tutte le colonne acquisite nella tabella di origine e, se è stato definito un ruolo di controllo per l'istanza di acquisizione, l'appartenenza a tale ruolo del database. Se il chiamante non dispone delle autorizzazioni per visualizzare i dati di origine, la funzione restituisce l'errore 22981 (Oggetto inesistente o accesso negato).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente sono restituite le informazioni sulle colonne acquisite nell'istanza di acquisizione `HumanResources_Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_get_captured_columns   
    @capture_instance = N'HumanResources_Employee';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. sp_cdc_help_change_data_capture &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
