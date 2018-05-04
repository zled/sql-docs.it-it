---
title: MSpeer_conflictdetectionconfigrequest (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- MSpeer_conflictdetectionconfigrequest_TSQL
- MSpeer_conflictdetectionconfigrequest
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_conflictdetectionconfigurerequest
ms.assetid: 83afa0ca-707e-4468-a888-228268ed4e10
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6f4b5918797cee78394384a37d707b72de5620d0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mspeerconflictdetectionconfigrequest-transact-sql"></a>MSpeer_conflictdetectionconfigrequest (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilizzata nella replica peer-to-peer per tenere traccia delle richieste di configurazione a livello di topologia per una pubblicazione. Questa tabella è archiviata nel database di pubblicazione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|id|**int**|Identifica una richiesta di configurazione in conflitto. La colonna request_id in [MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md) utilizza questo valore.|  
|pubblicazione|**sysname**|Nome della pubblicazione da cui viene originata la richiesta di configurazione in conflitto.|  
|sent_date|**datetime**|Data e ora di invio della richiesta di configurazione in conflitto.|  
|timeout|**int**|Tempo di attesa da parte di una procedura per la restituzione delle informazioni sul conflitto da tutti i peer.|  
|modified_date|**datetime**|Data e ora del completamento di una fase.|  
|progress_phase|**nvarchar(32)**|Identifica la fase di elaborazione corrente utilizzando uno dei valori seguenti:<br /><br /> Started<br /><br /> Esplorazione topologia<br /><br /> Raccolta stato<br /><br /> Stato raccolto|  
|phase_timed_out|**bit**|Indica se si è verificato un timeout nella fase corrente.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
