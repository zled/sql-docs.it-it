---
title: ddl_history (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cdc.ddl_history_TSQL
- cdc.ddl_history
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.ddl_history
ms.assetid: cb97ea71-da2f-441a-bbd2-db1f5f48ab49
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26ce592636c837f74cbbc8980b5d7cbd8742f78a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="cdcddlhistory-transact-sql"></a>cdc.ddl_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni modifica DDL (Data Definition Language) apportata a tabelle abilitate per l'acquisizione dei dati delle modifiche. È possibile utilizzare questa tabella per determinare quando si è verificata una modifica DDL su una tabella di origine e la modifica effettuata. Per le tabelle di origine per cui non sono state eseguite modifiche DDL non esistono voci in questa tabella.  
  
 È consigliabile non eseguire una query direttamente sulle tabelle di sistema. Eseguire invece il [sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md) stored procedure.  
   
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**source_object_id**|**int**|ID della tabella di origine alla quale è stata applicata la modifica DDL.|  
|**object_id**|**int**|ID della tabella delle modifiche associata a un'istanza di acquisizione per la tabella di origine.|  
|**required_column_update**|**bit**|Indica che il tipo di dati di una colonna acquisita è stato modificato nella tabella di origine. Questa modifica ha modificato la colonna nella tabella delle modifiche.|  
|**ddl_command**|**nvarchar(max)**|Istruzione DDL applicata alla tabella di origine.|  
|**ddl_lsn**|**binary(10)**|Il numero di sequenza del file di log (LSN) associato all'impegno della modifica DDL.|  
|**ddl_time**|**datetime**|Data e ora di esecuzione della modifica DDL nella tabella di origine.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. sp_cdc_help_change_data_capture &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [CDC. fn_cdc_get_all_changes_ &#60; capture_instance &#62;  &#40; Transact-SQL &#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
