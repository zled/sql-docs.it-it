---
title: MSqreader_history (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSqreader_history
- MSqreader_history_TSQL
dev_langs: TSQL
helpviewer_keywords: MSqreader_history system table
ms.assetid: c5c91d39-513c-4a77-870b-c8ef74a1cd6b
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7c9615bb702c89d8b2a5be0087671df9d8a6a910
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="msqreaderhistory-transact-sql"></a>MSqreader_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSqreader_history** tabella contiene righe di cronologia per gli agenti di lettura coda associati al server di distribuzione locale. Questa tabella è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ID dell'agente di lettura coda.|  
|**publication_id**|**int**|ID della pubblicazione.|  
|**runstatus**|**int**|Stato di esecuzione dell'agente:<br /><br /> **1** = avvio.<br /><br /> **2** = esito positivo.<br /><br /> **3** = in corso.<br /><br /> **4** = inattivo.<br /><br /> **5** = nuovo tentativo.<br /><br /> **6** = esito negativo.|  
|**start_time**|**datetime**|Data e ora di inizio della sessione dell'agente.|  
|**time**|**datetime**|Data e ora dell'ultimo messaggio registrato.|  
|**duration**|**int**|Tempo trascorso, espresso in secondi, delle attività della sessione registrate.|  
|**commenti**|**nvarchar(255)**|Testo descrittivo.|  
|**transaction_id**|**nvarchar (40)**|ID della transazione archiviato insieme al messaggio, se applicabile.|  
|**transaction_status**|**int**|Stato della transazione.|  
|**transactions_processed**|**int**|Numero totale di transazioni elaborate durante la sessione.|  
|**commands_processed**|**int**|Numero totale di comandi elaborati durante la sessione.|  
|**delivery_rate**|**float(53)**|Numero medio di comandi recapitati al secondo.|  
|**transaction_rate**|**float(53)**|Velocità delle transazioni elaborate.|  
|**subscriber**|**sysname**|Nome del Sottoscrittore.|  
|**subscriberdb**|**sysname**|Nome del database di sottoscrizione.|  
|**error_id**|**int**|Se non è zero, il numero rappresenta un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] messaggio di errore.|  
|**timestamp**|**timestamp**|Colonna di tipo timestamp della tabella.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
