---
title: "Impostazione dell&#39;ordine di elaborazione degli articoli di merge | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "articoli [replica di SQL Server], ordine di elaborazione"
  - "replica di tipo merge [replica di SQL Server], ordine di elaborazione degli articoli"
ms.assetid: d151e2c5-cf50-4cb3-a829-8f32455dbd66
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# Impostazione dell&#39;ordine di elaborazione degli articoli di merge
  A partire da [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], è possibile ignorare l'ordine predefinito di elaborazione degli articoli per pubblicazioni di tipo merge. Ciò risulta utile, ad esempio, se si definisce l'integrità referenziale tramite trigger e tali trigger devono essere attivati in un determinato ordine.  
  
 **Per specificare l'ordine di elaborazione degli articoli**  
  
-   Programmazione Transact-SQL della replica: [specificare l'elaborazione dell'ordine di tabella articoli di Merge & #40; Programmazione Transact-SQL della replica & #41;](../../../relational-databases/replication/publish/specify the processing order of merge table articles.md)  
  
## Modalità di determinazione dell'ordine di elaborazione  
 Durante la sincronizzazione di tipo merge, gli articoli vengono elaborati per impostazione predefinita nell'ordine richiesto dalle dipendenze tra gli oggetti, inclusi i vincoli di integrità referenziale dichiarativa definiti nelle tabelle di base. L'elaborazione prevede l'enumerazione delle modifiche apportate a una tabella e quindi l'applicazione di tali modifiche. Se non è presente l'integrità referenziale dichiarativa ma esistono filtri join o record logici tra gli articoli di tabella, gli articoli vengono elaborati nell'ordine richiesto dai filtri e dai record logici. Gli articoli non correlati ad altri articoli tramite integrità referenziale Dichiarativa, filtri join, i record logici o altre dipendenze vengono elaborati in base il nome alternativo dell'articolo nel [sysmergearticles & #40; Transact-SQL & #41;](../../../relational-databases/system-tables/sysmergearticles-transact-sql.md) tabella di sistema.  
  
 Si consideri una pubblicazione che include le tabelle **SalesOrderHeader** e **SalesOrderDetail** con una colonna chiave primaria **SalesOrderID** nel **SalesOrderHeader** tabella e un'esterna corrispondente della colonna chiave **SalesOrderID** nel **SalesOrderDetail** tabella. Durante la sincronizzazione, replica di tipo merge impedisce le violazioni di chiave esterne inserendo nuove righe in **SalesOrderHeader** prima di inserire righe associate in **SalesOrderDetail**. Analogamente, le righe vengono eliminate da **SalesOrderDetail** prima della riga associata viene eliminata dal **SalesOrderHeader**.  
  
 In alcune applicazioni, tuttavia, l'integrità referenziale viene applicata tramite trigger di database o a livello di applicazione, anziché tramite integrità referenziale dichiarativa. Nel caso della pubblicazione sopra descritta, anziché l'integrità referenziale Dichiarativa, la **SalesOrderDetail** tabella potrebbe disporre di un trigger insert che garantisce la riga corrispondente nel **SalesOrderHeader** tabella esista prima di consentire un inserimento. **SalesOrderHeader** potrebbe disporre di un trigger delete che assicura che non siano presenti righe associate in **SalesOrderDetail** prima di consentire un'eliminazione. I trigger non vengono presi in considerazione nella replica di tipo merge per determinare l'ordine di elaborazione degli articoli, poiché non è possibile determinare il risultato del trigger finché non viene attivato. Analogamente, nella replica non possono essere considerati i vincoli definiti a livello di applicazione.  
  
 In caso di mantenimento dell'integrità referenziale tramite trigger o a livello di applicazione, è consigliabile specificare l'ordine in cui gli articoli devono essere elaborati. Nell'esempio di trigger, specificare che il **SalesOrderHeader** tabella deve essere elaborata prima **SalesOrderDetail**, poiché l'ordine degli articoli è basato sull'ordine di inserimento. Nella replica di tipo merge verrà automaticamente invertito l'ordine per le eliminazioni. La replica di tipo merge non avrà esito negativo se gli articoli non vengono ordinati, poiché l'agente di merge continua a elaborare gli articoli in caso di violazione di un vincolo e quindi ripete le operazioni non riuscite dopo l'elaborazione degli altri articoli. Specificando l'ordine degli articoli è semplicemente possibile evitare i successivi tentativi e l'elaborazione aggiuntiva associata. Se si specifica un ordine non corretto, ad esempio un ordine che determina l'elaborazione dei record di dettagli prima dei record di intestazione, la replica di tipo merge ripeterà l'elaborazione finché non avrà esito positivo.  
  
## Vedere anche  
 [Opzioni degli articoli per la replica di tipo merge](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Raggruppamento di modifiche alla righe correlate con record logici](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [Filtri join](../../../relational-databases/replication/merge/join-filters.md)  
  
  