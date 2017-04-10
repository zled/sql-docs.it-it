---
title: "Impostazione dell&#39;ordine di elaborazione degli articoli di tabelle di merge (programmazione Transact-SQL della replica) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
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
  - "articoli [replica di SQL Server], ordine di elaborazione"
  - "replica di tipo merge [replica di SQL Server], ordine di elaborazione degli articoli"
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Impostazione dell&#39;ordine di elaborazione degli articoli di tabelle di merge (programmazione Transact-SQL della replica)
  La replica di tipo merge consente di specificare l'ordine in cui gli articoli vengono elaborati dall'agente di merge durante il processo di sincronizzazione. È possibile assegnare a livello di programmazione un ordine a ogni articolo creato utilizzando le stored procedure di replica. Gli articoli vengono elaborati in ordine crescente in base al valore. Se due articoli hanno lo stesso valore, essi vengono elaborati simultaneamente. Per ulteriori informazioni, vedere [specificare l'elaborazione dell'ordine di articoli di Merge](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).  
  
### Per specificare l'ordine di elaborazione di un nuovo articolo di merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare un valore intero che rappresenta l'ordine di elaborazione dell'articolo per **@processing_order**. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Quando si creano articoli ordinati, è necessario lasciare gap tra i valori relativi all'ordine degli articoli. In questo modo risulta più agevole impostare nuovi valori in futuro. Ad esempio, se si dispone di tre articoli per cui è necessario specificare un ordine di elaborazione fisso, impostare il valore di **@processing_order** a 10, 20 e 30 anziché 1, 2 e 3, rispettivamente.  
  
### Per modificare l'ordine di elaborazione di un articolo di merge  
  
1.  Per determinare l'ordine di elaborazione di un articolo, eseguire [sp_helpmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) e prendere nota del valore di **processing_order** nel set di risultati.  
  
2.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare un valore di **processing_order** per **@property** e un valore integer che rappresenta l'ordine di elaborazione per **@value**.  
  
## Vedere anche  
 [Impostazione dell'ordine di elaborazione degli articoli di merge](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  