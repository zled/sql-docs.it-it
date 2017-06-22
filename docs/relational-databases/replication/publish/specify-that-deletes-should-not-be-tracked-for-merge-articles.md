---
title: Disattivare il rilevamento delle eliminazioni per gli articoli di merge | Microsoft Docs
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
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 285e91369dfc5572b0da94fc110ce8b9e720b8a6
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="specify-that-deletes-should-not-be-tracked-for-merge-articles"></a>Disattivare il rilevamento delle eliminazioni per gli articoli di merge
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Per impostazione predefinita, la replica di tipo merge consente di sincronizzare i comandi DELETE tra server di pubblicazione e Sottoscrittore. Con la replica di tipo merge le righe vengono mantenute nel database di sottoscrizione anche se sono state eliminate dalla pubblicazione e viceversa. È possibile specificare a livello di programmazione che i comandi DELETE vengano ignorati durante la creazione di un nuovo articolo oppure attivare questa funzionalità in un secondo momento utilizzando le stored procedure di replica.  
  
> [!IMPORTANT]  
>  L'attivazione di questa funzionalità causa la non convergenza pertanto i dati presenti nel Sottoscrittore non rifletteranno accuratamente i dati presenti nel server di pubblicazione. È necessario implementare un meccanismo personalizzato per la rimozione manuale delle righe eliminate.  
  
### <a name="to-specify-that-deletes-be-ignored-for-a-new-merge-article"></a>Per specificare che si desidera ignorare le eliminazioni per un nuovo articolo di merge  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare il valore **false** per il parametro **@delete_tracking**. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Se la tabella di origine di un articolo è già pubblicata in un'altra pubblicazione, il valore di **delete_tracking** deve essere uguale per entrambi gli articoli.  
  
### <a name="to-specify-that-deletes-be-ignored-for-an-existing-merge-article"></a>Per specificare che si desidera ignorare le eliminazioni per un articolo di merge esistente  
  
1.  Per determinare se la compensazione errori è abilitata per un articolo, eseguire [sp_helpmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) e prendere nota del valore di **delete_tracking** nel set di risultati. Se questo valore è **0**, le eliminazioni vengono già ignorate.  
  
2.  Se il valore ottenuto al passaggio 1 è **1**, eseguire [sp_changemergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) nel database di pubblicazione del server di pubblicazione. Specificare il valore **delete_tracking** per il parametro **@property**e il valore **false** per il parametro **@value**.  
  
    > [!NOTE]  
    >  Se la tabella di origine di un articolo è già pubblicata in un'altra pubblicazione, il valore di **delete_tracking** deve essere uguale per entrambi gli articoli.  
  
## <a name="see-also"></a>Vedere anche  
 [Ottimizzare le prestazioni della replica di tipo merge con il rilevamento condizionale delle eliminazioni](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
