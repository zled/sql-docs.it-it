---
title: IHsubscriptions (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- IHsubscriptions_TSQL
- IHsubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- IHsubscriptions system table
ms.assetid: 9ec21119-35f1-4e39-abaa-b2c790c485b1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9487ac5859c0bd35cbcbfc326f6a175fc480f17d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="ihsubscriptions-transact-sql"></a>IHsubscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **IHsubscriptions** tabella di sistema contiene una riga per ogni sottoscrizione di una pubblicazione da un Server di pubblicazione non SQL utilizzando il server di distribuzione corrente. Questa tabella è archiviata nel database di distribuzione.  
  
## <a name="definition"></a>Definizione  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|Identifica in modo univoco un articolo pubblicato.|  
|**srvID**|**smallint**|ID del Sottoscrittore.|  
|**dest_db**|**sysname**|Nome del database di destinazione.|  
|**login_name**|**sysname**|Nome dell'account di accesso utilizzato quando si aggiunge la sottoscrizione.|  
|**distribution_jobid**|**Binary (16)**|ID del processo dell'agente di distribuzione|  
|**timestamp**|**timestamp**|Data e ora di creazione della sottoscrizione.|  
|**queued_reinit**|**bit**|Specifica se l'articolo è contrassegnato per l'inizializzazione o la reinizializzazione. Il valore **1** specifica che l'articolo sottoscritto è contrassegnato per l'inizializzazione o la reinizializzazione.|  
|**status**|**tinyint**|Stato della sottoscrizione:<br /><br /> **0** = inattivo.<br /><br /> **1** = sottoscritto.<br /><br /> **2** = attivo.|  
|**sync_type**|**tinyint**|Tipo di sincronizzazione iniziale:<br /><br /> **1** = automatica.<br /><br /> **2** = none.|  
|**subscription_type**|**int**|Tipo di sottoscrizione:<br /><br /> **0** = push: l'agente di distribuzione viene eseguito nel Sottoscrittore.<br /><br /> **1** = pull: l'agente di distribuzione viene eseguito nel server di distribuzione.|  
|**update_mode**|**tinyint**|Modalità di aggiornamento:<br /><br /> **0** = sola lettura.<br /><br /> **1** = aggiornamento immediato.|  
|**loopback_detection**|**bit**|Si applica alle sottoscrizioni che fanno parte di una topologia di replica transazionale bidirezionale. Il rilevamento di loopback determina se l'agente di distribuzione deve inviare nuovamente al Sottoscrittore le transazioni provenienti dal Sottoscrittore:<br /><br /> **0** = invia nuovamente.<br /><br /> **1** = non ha restituito.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40; Transact-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [stored procedure sp_addsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_helpsubscription &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
