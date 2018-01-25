---
title: Specificare l'ordine di elaborazione degli articoli di merge| Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: d151e2c5-cf50-4cb3-a829-8f32455dbd66
caps.latest.revision: "34"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4476f6aaa996dff5ed88258a2cb9430a62774cd
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="specify-the-processing-order-of-merge-articles"></a>Impostazione dell'ordine di elaborazione degli articoli di merge
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] A partire da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], è possibile eseguire l'override dell'ordine predefinito dell'elaborazione degli articoli per le pubblicazioni di tipo merge. Ciò risulta utile, ad esempio, se si definisce l'integrità referenziale tramite trigger e tali trigger devono essere attivati in un determinato ordine.  
  
 **Per specificare l'ordine di elaborazione degli articoli**  
  
-   Programmazione Transact-SQL della replica: [Specificare l'ordine di elaborazione degli articoli di tabelle di merge &#40;programmazione Transact-SQL della replica&#41;](../../../relational-databases/replication/publish/specify-the-processing-order-of-merge-table-articles.md)  
  
## <a name="how-processing-order-is-determined"></a>Modalità di determinazione dell'ordine di elaborazione  
 Durante la sincronizzazione di tipo merge, gli articoli vengono elaborati per impostazione predefinita nell'ordine richiesto dalle dipendenze tra gli oggetti, inclusi i vincoli di integrità referenziale dichiarativa definiti nelle tabelle di base. L'elaborazione prevede l'enumerazione delle modifiche apportate a una tabella e quindi l'applicazione di tali modifiche. Se non è presente l'integrità referenziale dichiarativa ma esistono filtri join o record logici tra gli articoli di tabella, gli articoli vengono elaborati nell'ordine richiesto dai filtri e dai record logici. Gli articoli non correlati ad altri articoli tramite integrità referenziale dichiarativa, filtri join, record logici o altre dipendenze vengono elaborati in base al nome alternativo dell'articolo nella tabella di sistema [sysmergearticles &#40;Transact-SQL&#41;](../../../relational-databases/system-tables/sysmergearticles-transact-sql.md).  
  
 Si consideri una pubblicazione in cui sono incluse le tabelle **SalesOrderHeader** e **SalesOrderDetail** con una colonna chiave primaria **SalesOrderID** nella tabella **SalesOrderHeader** e una colonna chiave esterna **SalesOrderID** corrispondente nella tabella **SalesOrderDetail** . Durante la sincronizzazione, la replica di tipo merge impedisce le violazioni della chiave esterna inserendo nuove righe in **SalesOrderHeader** prima dell'inserimento delle righe associate in **SalesOrderDetail**. Analogamente, le righe vengono eliminate da **SalesOrderDetail** prima dell'eliminazione delle righe associate da **SalesOrderHeader**.  
  
 In alcune applicazioni, tuttavia, l'integrità referenziale viene applicata tramite trigger di database o a livello di applicazione, anziché tramite integrità referenziale dichiarativa. Nel caso della pubblicazione sopra descritta, anziché utilizzare l'integrità referenziale dichiarativa, la tabella **SalesOrderDetail** potrebbe disporre di un trigger di inserimento in grado di verificare l'esistenza della riga associata nella tabella **SalesOrderHeader** prima di consentire un inserimento. **SalesOrderHeader** potrebbe disporre di un trigger di eliminazione in grado di verificare l'assenza di righe associate in **SalesOrderDetail** prima di consentire un'eliminazione. I trigger non vengono presi in considerazione nella replica di tipo merge per determinare l'ordine di elaborazione degli articoli, poiché non è possibile determinare il risultato del trigger finché non viene attivato. Analogamente, nella replica non possono essere considerati i vincoli definiti a livello di applicazione.  
  
 In caso di mantenimento dell'integrità referenziale tramite trigger o a livello di applicazione, è consigliabile specificare l'ordine in cui gli articoli devono essere elaborati. Nell'esempio con i trigger, verrà specificato che la tabella **SalesOrderHeader** deve essere elaborata prima di **SalesOrderDetail**, poiché l'ordine degli articoli è basato sull'ordine di inserimento. Nella replica di tipo merge verrà automaticamente invertito l'ordine per le eliminazioni. La replica di tipo merge non avrà esito negativo se gli articoli non vengono ordinati, poiché l'agente di merge continua a elaborare gli articoli in caso di violazione di un vincolo e quindi ripete le operazioni non riuscite dopo l'elaborazione degli altri articoli. Specificando l'ordine degli articoli è semplicemente possibile evitare i successivi tentativi e l'elaborazione aggiuntiva associata. Se si specifica un ordine non corretto, ad esempio un ordine che determina l'elaborazione dei record di dettagli prima dei record di intestazione, la replica di tipo merge ripeterà l'elaborazione finché non avrà esito positivo.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni degli articoli per la replica di tipo merge](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Raggruppare modifiche alle righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [Join Filters](../../../relational-databases/replication/merge/join-filters.md)  
  
  
