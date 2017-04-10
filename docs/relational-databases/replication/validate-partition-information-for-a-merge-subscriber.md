---
title: "Convalida delle informazioni sulle partizioni per un Sottoscrittore di tipo merge | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "convalida di dati di replica di tipo merge [replica di SQL Server], partizioni"
  - "filtri con parametri [replica di SQL Server], convalida di informazioni di partizione"
  - "convalida di informazioni di partizione"
ms.assetid: c059553e-df2c-4333-ba79-e8d6e2890c34
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Convalida delle informazioni sulle partizioni per un Sottoscrittore di tipo merge
  Quando si definisce un filtro di riga con parametri per una pubblicazione di tipo merge, si utilizza una funzione che fa riferimento a informazioni sul Sottoscrittore, ad esempio il nome di accesso del Sottoscrittore. Per impostazione predefinita, le informazioni sul Sottoscrittore vengono convalidate dalla replica in base a tale funzione prima di ogni sincronizzazione e ogni volta che uno snapshot viene applicato al Sottoscrittore. Il processo di convalida garantisce il partizionamento corretto dei dati per ogni Sottoscrittore. Comportamento di convalida è controllato dal **validate_subscriber_info** Proprietà pubblicazione, che può essere modificato utilizzando [sp_changemergepublication & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) o il **Opzioni di sottoscrizione** pagina del **Proprietà pubblicazione** la finestra di dialogo. Per ulteriori informazioni sulla modifica delle proprietà di pubblicazione, vedere [visualizzare e modificare le proprietà di pubblicazione](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
## Funzionamento della convalida delle partizioni  
 Quando una pubblicazione viene filtrata, ad esempio, utilizzando la funzione **SUSER_SNAME ()**, l'agente di Merge applica lo snapshot iniziale per ogni sottoscrittore in base ai dati che sono validi per il **SUSER_SNAME ()** espressione.  
  
 Se la convalida è abilitata, quando il Sottoscrittore si riconnette al server di pubblicazione per la successiva sincronizzazione, l'agente di merge convalida le informazioni nel Sottoscrittore e garantisce che la partizione di ogni Sottoscrittore corrisponda a quella ricevuta nello snapshot iniziale. Per ogni successiva applicazione di snapshot o merge, l'agente di merge convalida la partizione di ogni Sottoscrittore.  
  
 Se l'agente di merge rileva che la funzione utilizzata nell'espressione di filtro restituisce un valore diverso rispetto allo snapshot iniziale, l'applicazione di snapshot o merge ha esito negativo e potrebbe essere necessaria la reinizializzazione della sottoscrizione del Sottoscrittore. La reinizializzazione può risultare necessaria per evitare i problemi che possono verificarsi in caso di modifica delle impostazioni di merge di un Sottoscrittore. Può tuttavia rivelarsi sufficiente modificare le informazioni nel Sottoscrittore, ad esempio il nome di accesso, ripristinando il valore utilizzato al momento dello snapshot originale.  
  
 Quando l'agente di merge convalida una partizione, oltre a convalidare la partizione rispetto ai valori restituiti dalle funzioni utilizzate nelle espressioni di filtro, controlla se lo snapshot è stato generato prima di modifiche che ne compromettono la validità, come operazioni di pulizia dei metadati o modifiche dello schema. Se uno snapshot partizionato è obsoleto, l'agente di merge restituirà un errore e sarà necessario rigenerare uno snapshot partizionato per il Sottoscrittore in base a uno snapshot regolare corrente.  
  
## Vedere anche  
 [Amministrazione & #40; Replica & #41;](../../relational-databases/replication/administration/administration-replication.md)   
 [Procedure consigliate per l'amministrazione della replica](../../relational-databases/replication/administration/best-practices-for-replication-administration.md)   
 [Reinizializzare le sottoscrizioni](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Convalida dei dati replicati](../../relational-databases/replication/validate-replicated-data.md)  
  
  