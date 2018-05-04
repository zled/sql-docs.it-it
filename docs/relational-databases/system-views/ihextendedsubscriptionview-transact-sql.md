---
title: IHextendedSubscriptionView (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- IHextendedSubscriptionView_TSQL
- IHextendedSubscriptionView
dev_langs:
- TSQL
helpviewer_keywords:
- IHextendedSubscriptionView view
ms.assetid: 124756a4-463a-4a81-bf5b-de7e8ffc7a62
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fa0db6a6fbb93c683271de492c19184ac7b68f1a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="ihextendedsubscriptionview-transact-sql"></a>IHextendedSubscriptionView (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **IHextendedSubscriptionView** visualizzazione espone informazioni sulla sottoscrizione di una pubblicazione non SQL Server. Questa vista è archiviata nel **distribuzione** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|ID univoco di un articolo.|  
|**dest_db**|**sysname**|Nome del database di destinazione.|  
|**srvid**|**smallint**|ID univoco di un Sottoscrittore.|  
|**login_name**|**sysname**|Account di accesso utilizzato per la connessione a un Sottoscrittore.|  
|**distribution_jobid**|**binary**|Identifica il processo dell'agente di distribuzione.|  
|**publisher_database_id**|**int**|Identifica il database di pubblicazione.|  
|**subscription_type**|**int**|Tipo di sottoscrizione:<br /><br /> **0** = push: l'agente di distribuzione viene eseguito nel Sottoscrittore.<br /><br /> **1** = pull: l'agente di distribuzione viene eseguito nel server di distribuzione.|  
|**sync_type**|**tinyint**|Tipo di sincronizzazione iniziale:<br /><br /> **1** = automatica<br /><br /> **2** = nessuno|  
|**status**|**tinyint**|Stato della sottoscrizione:<br /><br /> **0** = inattivo<br /><br /> **1** = sottoscritto<br /><br /> **2** = attivo|  
|**snapshot_seqno_flag**|**bit**|Indica se viene utilizzato un numero di sequenza dello snapshot.|  
|**independent_agent**|**bit**|Specifica se per la pubblicazione è disponibile un agente di distribuzione autonomo.<br /><br /> **0** = la pubblicazione utilizza un agente di distribuzione condiviso, e ogni coppia database del server di pubblicazione/sottoscrittore del database dispone di un solo agente condiviso.<br /><br /> **1** = è disponibile un agente di distribuzione autonomo per questa pubblicazione.|  
|**subscription_time**|**datetime**|Solo per uso interno.|  
|**loopback_detection**|**bit**|Si applica alle sottoscrizioni che fanno parte di una topologia di replica transazionale bidirezionale. Il rilevamento di loopback determina se l'agente di distribuzione deve inviare nuovamente al Sottoscrittore le transazioni provenienti dal Sottoscrittore:<br /><br /> **1** = non restituisce le transazioni.<br /><br /> **0** = restituisce le transazioni.|  
|**agent_id**|**int**|ID univoco dell'agente di distribuzione.|  
|**update_mode**|**tinyint**|Indica il tipo di modalità di aggiornamento. I possibili valori sono i seguenti:<br /><br /> **0** = sola lettura.<br /><br /> **1** = aggiornamento immediato.<br /><br /> **2** = aggiornamento in coda tramite MSMQ.<br /><br /> **3** = controllo immediato aggiornare con aggiornamento in coda come failover tramite MSMQ.<br /><br /> **4** = aggiornamento in coda tramite la coda SQL Server.<br /><br /> **5** = aggiornamento immediato con failover dell'aggiornamento in coda, tramite la coda SQL Server.|  
|**publisher_seqno**|**varbinary(16)**|Numero di sequenza della transazione nel server di pubblicazione per questa sottoscrizione.|  
|**ss_cplt_seqno**|**varbinary(16)**|Numero di sequenza utilizzato per indicare il completamento dell'elaborazione simultanea degli snapshot.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
