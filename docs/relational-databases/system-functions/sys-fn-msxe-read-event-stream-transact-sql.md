---
title: sys.fn_MSxe_read_event_stream (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_MSxe_read_event_stream_TSQL
- sys.fn_MSxe_read_event_stream_TSQL
- sys.fn_MSxe_read_event_stream
- fn_MSxe_read_event_stream
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_MSxe_read_event_stream
- fn_MSxe_read_event_stream
ms.assetid: 5edb1162-625a-41e0-8ec9-1edc8ab9a74a
caps.latest.revision: 9
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7411c782bedc583ea8ddb0aaa4e0e92c46d73453
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysfnmsxereadeventstream-transact-sql"></a>sys.fn_MSxe_read_event_stream (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gli eventi estesi forniscono una funzione con valori di tabella per l'utilizzo interno da parte dell'interfaccia utente degli eventi estesi. La tabella non fornisce dati utilizzabili dagli utenti.  
  
 Per visualizzare dati evento, utilizzare uno degli elementi seguenti:  
  
-   Interfaccia utente per una nuova sessione di eventi estesi.  
  
-   Funzione con valori di tabella fn_xe_file_target_read_file. Per altre informazioni, vedere [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql.md).  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_MSxe_read_event_stream ( session_name)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Session_name*  
 Nome di una sessione eseguita nel server.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|Tipo|**Integer (4)**|Tipo di evento. Non ammette i valori Null.|  
|data|**Immagine (16)**|Dati immagine dell'evento. Ammette i valori Null.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste a gestione dinamica degli eventi estesi](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [Viste del catalogo degli eventi estesi &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Eventi estesi](../../relational-databases/extended-events/extended-events.md)  
  
  
