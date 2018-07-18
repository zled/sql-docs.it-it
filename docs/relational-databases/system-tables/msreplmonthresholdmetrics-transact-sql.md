---
title: MSreplmonthresholdmetrics (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- msreplmonthresholdmetrics_TSQL
- msreplmonthresholdmetrics
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplmonthresholdmetrics system table
ms.assetid: 0cc9b40a-36ce-485b-9bc2-d4abd5aa6727
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ea5e725b3d2ef1f719a96b577f88504d58dadf7f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="msreplmonthresholdmetrics-transact-sql"></a>MSreplmonthresholdmetrics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSreplmonthresholdmetrics** tabella definisce le metriche specificate per il monitoraggio della replica. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|Identifica una misurazione delle prestazioni di replica. Ecco i possibili valori:<br /><br /> **1** = expiration<br /><br /> **2** = latenza<br /><br /> **4** = mergeexpiration<br /><br /> **5** = mergeslowrunduration<br /><br /> **6** = mergefastrunduration<br /><br /> **7** = mergefastrunspeed<br /><br /> **8** = mergeslowrunspeed|  
|**title**|**sysname**|Nome della misurazione delle prestazioni di replica.|  
|**warningbitstatus**|**int**|Identificatore bit per bit utilizzato per generare un avviso per la violazione del valore soglia di una delle misurazioni seguenti:<br /><br /> **1** = expiration-una sottoscrizione di una pubblicazione transazionale ha superato il periodo di memorizzazione rispetto al valore soglia consentito, come percentuale del periodo di memorizzazione.<br /><br /> **2** = latency-il tempo necessario per replicare i dati da un server di pubblicazione transazionale al sottoscrittore supera la soglia, espresso in secondi.<br /><br /> **4** = mergeexpiration-una sottoscrizione di una pubblicazione di tipo merge ha superato il periodo di memorizzazione rispetto al valore soglia consentito, come percentuale del periodo di memorizzazione.<br /><br /> **8** = mergefastrunduration-il tempo impiegato per completare la sincronizzazione di una sottoscrizione di tipo merge supera la soglia, espresso in secondi, su una connessione di rete veloce.<br /><br /> **16** = mergeslowrunduration-il tempo impiegato per completare la sincronizzazione di una sottoscrizione di tipo merge supera la soglia, espresso in secondi, su una connessione di rete lenta o remota.<br /><br /> **32** = mergefastrunspeed – la velocità di recapito delle righe durante la sincronizzazione di una sottoscrizione di tipo merge è minore della soglia, in righe al secondo, su una connessione di rete veloce.<br /><br /> **64** = mergeslowrunspeed – la velocità di recapito delle righe durante la sincronizzazione di una sottoscrizione di tipo merge è minore della soglia, in righe al secondo, su una connessione di rete lenta o remota.|  
|**alertmessageid**|**int**|ID del messaggio di errore visualizzato quando si verifica la condizione per la generazione di un avviso per la violazione del valore soglia.|  
|**description**|**nvarchar(3000)**|Descrizione della misurazione delle prestazioni di replica.|  
|**default_value**|**sql_variant**|Valore predefinito della misurazione delle prestazioni di replica.|  
|**MIN_VALUE**|**sql_variant**|Valore minimo per una misurazione delle prestazioni di replica con limitazioni.|  
|**MAX_VALUE**|**sql_variant**|Valore massimo per una misurazione delle prestazioni di replica con limitazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
