---
title: "Configurazione del processo del set di transazioni per un server di pubblicazione Oracle (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_publisherproperty"
  - "pubblicazione Oracle [replica di SQL Server], configurazione"
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Configurazione del processo del set di transazioni per un server di pubblicazione Oracle (programmazione Transact-SQL della replica)
  Il **Xactset** processo è un processo di database Oracle creato dalla replica eseguita in un server di pubblicazione Oracle per creare set di transazioni quando l'agente di lettura Log non è connesso al server di pubblicazione. È possibile abilitare e configurare questo processo a livello di programmazione dal server di distribuzione, utilizzando le stored procedure di replica. Per ulteriori informazioni, vedere [ottimizzazione delle prestazioni per server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
### Per abilitare il processo del set di transazioni  
  
1.  Nel server di pubblicazione Oracle, impostare il **job_queue_processes** parametro di inizializzazione per un valore sufficiente per consentire l'esecuzione del processo Xactset. Per ulteriori informazioni su questo parametro, vedere la documentazione del database relativa al server di pubblicazione Oracle.  
  
2.  Nel server di distribuzione, eseguire [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, un valore di **xactsetbatching** per **@propertyname**, e il valore **abilitato** per **@propertyvalue**.  
  
3.  Nel server di distribuzione, eseguire [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, un valore di **xactsetjobinterval** per **@propertyname**, e l'intervallo del processo, espresso in minuti, per **@propertyvalue**.  
  
4.  Nel server di distribuzione, eseguire [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, un valore di **xactsetjob** per **@propertyname**, e il valore **abilitato** per **@propertyvalue**.  
  
### Per configurare il processo del set di transazioni  
  
1.  (Facoltativo) Nel server di distribuzione, eseguire [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**. Verranno restituite le proprietà del **Xactset** processo nel server di pubblicazione.  
  
2.  Nel server di distribuzione, eseguire [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, il nome della proprietà del processo Xactset impostato per **@propertyname**, e la nuova impostazione per **@propertyvalue**.  
  
3.  (Facoltativo) Ripetere il passaggio 2 per ogni proprietà del processo Xactset impostata. Quando si modifica il **xactsetjobinterval** proprietà, è necessario riavviare il processo nel server di pubblicazione Oracle per il nuovo intervallo diventino effettive.  
  
### Per visualizzare le proprietà del processo del set di transazioni  
  
1.  Nel server di distribuzione, eseguire [sp_helpxactsetjob](../../../relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**.  
  
### Per disabilitare il processo del set di transazioni  
  
1.  Nel server di distribuzione, eseguire [sp_publisherproperty & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md). Specificare il nome del server di pubblicazione Oracle per **@publisher**, un valore di **xactsetjob** per **@propertyname**, e il valore **disabilitato** per **@propertyvalue**.  
  
## Esempio  
 Nell'esempio seguente viene abilitato il processo `Xactset` e viene impostato un intervallo di tre minuti tra le esecuzioni.  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../relational-databases/replication/codesnippet/tsql/configure-the-transactio_1.sql)]  
  
## Vedere anche  
 [Ottimizzazione delle prestazioni per i server di pubblicazione Oracle](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)   
 [Concetti di base relativi alle stored procedure del sistema di replica](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  