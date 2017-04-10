---
title: "Valori HOST_NAME | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.hostnamevalue.f1"
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Valori HOST_NAME
  Le pubblicazioni di tipo merge provviste di filtri con parametri utilizzano la funzione SUSER_SNAME() e/o HOST_NAME() per filtrare i dati. La funzione viene specificata in Creazione guidata nuova pubblicazione oppure nella finestra di dialogo **Proprietà pubblicazione** .  
  
 Per impostazione predefinita, la funzione HOST_NAME() restituisce il nome del computer che esegue la connessione al server di pubblicazione. Se si utilizzano filtri con parametri, è possibile sostituire questo valore indicandone uno diverso in questa pagina della creazione guidata. La funzione HOST_NAME() restituisce quindi il valore specificato anziché il nome del computer. Per ulteriori informazioni, vedere la sezione "Sostituzione del valore di HOST_NAME ()" di [i filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
> [!NOTE]  
>  Se si sostituisce il valore HOST_NAME(), tutte le chiamate alla funzione HOST_NAME() restituiranno il valore specificato dall'utente. Verificare che il funzionamento di altre applicazioni non dipenda dal fatto che HOST_NAME() restituisca il nome del computer.  
  
## Opzioni  
 **Proprietà sottoscrizione**  
 Immettere un valore per ogni sottoscrittore presente la **valore HOST_NAME** colonna o accettare quello predefinito, ovvero il nome del computer del sottoscrittore.  
  
## Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [HOST_NAME & #40; Transact-SQL & #41;](../../t-sql/functions/host-name-transact-sql.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  