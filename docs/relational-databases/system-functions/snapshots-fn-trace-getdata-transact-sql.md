---
title: snapshots.fn_trace_getdata (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- snapshots.fn_trace_getdata
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots.fn_trace_getdata function
ms.assetid: ac28ef48-f4f4-4bf2-ba22-d44e1be88172
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0c6abb9a761023cca125ffae381ea8c72b0582d6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="snapshotsfntracegetdata-transact-sql"></a>snapshots.fn_trace_getdata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa funzione restituisce tutti gli eventi acquisiti per la traccia specificata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
snapshots.fn_trace_gettable ( trace_info_id, start_time, end_time )  
```  
  
## <a name="arguments"></a>Argomenti  
 *trace_info_id*  
 L'identificatore univoco per la chiave primaria nella tabella trace_info i dati di gestione del data warehouse del database. *trace_info_id* viene **int**.  
  
 *start_time*  
 Ora di avvio della traccia. *start_time* viene **datetime**.  
  
 *end_time*  
 Ora di fine della traccia. *end_time* viene **datetime**.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|\<Tutte le colonne di traccia >|\<Varia >|Dati di traccia della tabella snapshots.trace_data nel database del data warehouse di gestione.<br /><br /> È possibile ottenere un elenco di colonne per la traccia specificata mediante la query seguente:<br /><br /> `SELECT * FROM sys.trace_columns`<br /><br /> **Nota:** le colonne che vengono restituite dalla funzione snapshots. fn_trace_gettable corrispondono ai valori nella colonna name nella vista di sistema trace_columns. L'unica differenza è che la colonna GroupID non viene restituita dalla funzione.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede l'autorizzazione SELECT per mdw_reader.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)  
  
  
