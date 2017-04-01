---
title: "Disattivazione del rilevamento delle eliminazioni per gli articoli di merge (programmazione Transact-SQL della replica) | Microsoft Docs"
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
  - "rilevamento condizionale di eliminazioni [replica di SQL Server]"
  - "replica di tipo merge [replica di SQL Server], rilevamento condizionale di eliminazioni"
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Disattivazione del rilevamento delle eliminazioni per gli articoli di merge (programmazione Transact-SQL della replica)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Per impostazione predefinita, la replica di tipo merge consente di sincronizzare i comandi DELETE tra server di pubblicazione e Sottoscrittore. Con la replica di tipo merge le righe vengono mantenute nel database di sottoscrizione anche se sono state eliminate dalla pubblicazione e viceversa. È possibile specificare a livello di programmazione che i comandi DELETE vengano ignorati durante la creazione di un nuovo articolo oppure attivare questa funzionalità in un secondo momento utilizzando le stored procedure di replica.  
  
> [!IMPORTANT]  
>  L'attivazione di questa funzionalità causa la non convergenza pertanto i dati presenti nel Sottoscrittore non rifletteranno accuratamente i dati presenti nel server di pubblicazione. È necessario implementare un meccanismo personalizzato per la rimozione manuale delle righe eliminate.  
  
### Per specificare che si desidera ignorare le eliminazioni per un nuovo articolo di merge  
  
1.  Server di pubblicazione nel database di pubblicazione, eseguire [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Specificare un valore di **false** per **@delete_tracking**. Per altre informazioni, vedere [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
    > [!NOTE]  
    >  Se la tabella di origine per un articolo è già pubblicata in un'altra pubblicazione, il valore di **delete_tracking** deve essere uguale per entrambi gli articoli.  
  
### Per specificare che si desidera ignorare le eliminazioni per un articolo di merge esistente  
  
1.  Per determinare se compensazione errori è attivata per un articolo, eseguire [sp_helpmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) e prendere nota del valore di **delete_tracking** nel set di risultati. Se questo valore è **0**, le eliminazioni vengono già ignorate.  
  
2.  Se il valore ottenuto al passaggio 1 è **1**, eseguire [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) nel server di pubblicazione nel database di pubblicazione. Specificare un valore di **delete_tracking** per **@property**, e il valore **false** per **@value**.  
  
    > [!NOTE]  
    >  Se la tabella di origine per un articolo è già pubblicata in un'altra pubblicazione, il valore di **delete_tracking** deve essere uguale per entrambi gli articoli.  
  
## Vedere anche  
 [Ottimizzazione delle prestazioni della replica di tipo merge con il rilevamento condizionale delle eliminazioni](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  