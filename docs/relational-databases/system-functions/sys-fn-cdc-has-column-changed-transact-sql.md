---
title: sys.fn_cdc_has_column_changed (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- sys.fn_cdc_has_column_changed_TSQL
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed_TSQL
- fn_cdc_has_column_changed
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_has_column_changed
- fn_cdc_has_column_changed
ms.assetid: 2b9e6278-050d-4ffc-8d1a-09606180facc
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 22c44bf41cbb88098135f8a44432cad0acbc1fea
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="sysfncdchascolumnchanged-transact-sql"></a>sys.fn_cdc_has_column_changed (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rileva se la maschera di aggiornamento specificata indica che la colonna specificata è stata aggiornata nella riga della modifica associata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_cdc_has_column_changed ( 'capture_instance','column_name' , update_mask )  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *capture_instance* **'**  
 Nome dell'istanza di acquisizione. *capture_instance* è **sysname**.  
  
 **'** *column_name* **'**  
 Colonna acquisita dell'istanza di acquisizione specificata in base alla quale creare un report. *column_name* è **sysname**.  
  
 *update_mask*  
 Maschera che identifica le colonne aggiornate in qualsiasi riga della modifica associata. *update_mask* è **varbinary(128)**.  
  
## <a name="return-type"></a>Tipo restituito  
 **bit**  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare questa funzione per estrarre informazioni da una maschera di aggiornamento restituita in una query sui dati delle modifiche. La maschera di aggiornamento è molto utile in fase di post-elaborazione, quando è necessario sapere se una particolare colonna della riga della modifica associata è stata modificata. Per altre informazioni, vedere [Informazioni su Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md).  
  
 Quando queste informazioni verranno restituite come parte di una query di dati di modifica, è consigliabile utilizzare le funzioni [Sys. fn_cdc_get_column_ordinal](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md) e [Sys. fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md) anziché questa funzione. Utilizzare la funzione fn_cdc_get_column_ordinal prima di eseguire una query sui dati delle modifiche in modo che il numero ordinale di colonna desiderato venga calcolato solo una volta. Utilizzare fn_cdc_is_bit_set all'interno della query per estrarre informazioni dalla maschera di aggiornamento per ogni riga restituita.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server sysadmin o al ruolo predefinito del database db_owner. Per tutti gli altri utenti, è richiesta l'autorizzazione SELECT su tutte le colonne acquisite nella tabella di origine e, se è stato definito un ruolo di controllo per l'istanza di acquisizione, l'appartenenza a tale ruolo del database.  
  
## <a name="see-also"></a>Vedere anche  
 [cdc.&#60;capture_instance&#62;_CT &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)   
 [cdc.captured_columns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/cdc-captured-columns-transact-sql.md)  
  
  
