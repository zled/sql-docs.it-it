---
title: Specificare l&quot;ordine di elaborazione degli articoli di tabelle di merge| Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: 9fe576a2-f5fb-4fdf-bd7d-cb322021b669
caps.latest.revision: 33
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e84aea86e02abc3820ec615bbcfbe1c41a5cdfd7
ms.lasthandoff: 04/11/2017

---
# <a name="specify-the-processing-order-of-merge-table-articles"></a>Specificare l'ordine di elaborazione degli articoli di tabelle di merge
  La replica di tipo merge consente di specificare l'ordine in cui gli articoli vengono elaborati dall'agente di merge durante il processo di sincronizzazione. È possibile assegnare a livello di programmazione un ordine a ogni articolo creato utilizzando le stored procedure di replica. Gli articoli vengono elaborati in ordine crescente in base al valore. Se due articoli hanno lo stesso valore, essi vengono elaborati simultaneamente. Per altre informazioni, vedere [Specificare l'ordine di elaborazione degli articoli di merge](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md).  
  
### <a name="to-specify-the-processing-order-for-a-new-merge-article"></a>Per specificare l'ordine di elaborazione di un nuovo articolo di merge  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare un valore integer che rappresenta l'ordine di elaborazione per l'articolo per **@processing_order**. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Quando si creano articoli ordinati, è necessario lasciare gap tra i valori relativi all'ordine degli articoli. In questo modo risulta più agevole impostare nuovi valori in futuro. Se ad esempio si dispone di tre articoli per cui è necessario specificare un ordine di elaborazione fisso, impostare il valore di **@processing_order** su 10, 20 e 30 anziché rispettivamente su 1, 2 e 3.  
  
### <a name="to-change-the-processing-order-of-a-merge-article"></a>Per modificare l'ordine di elaborazione di un articolo di merge  
  
1.  Per determinare l'ordine di elaborazione di un articolo, eseguire [sp_helpmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) e prendere nota del valore di **processing_order** nel set di risultati.  
  
2.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_changemergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Specificare il valore **processing_order** per **@property** e un valore integer che rappresenta l'ordine di elaborazione per **@value**.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare l'ordine di elaborazione degli articoli di merge](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)  
  
  