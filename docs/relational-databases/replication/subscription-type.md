---
title: "Tipo di sottoscrizione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.subscriptiontype.f1"
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Tipo di sottoscrizione
  Replica di tipo merge offre due tipi di sottoscrizione: server e client (a cui le versioni precedenti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come globali e locali, rispettivamente). I Sottoscrittori con una sottoscrizione di tipo server sono in grado di:  
  
-   Ripubblicare i dati di altri Sottoscrittori.  
  
-   Fungere da partner di sottoscrizione alternativi.  
  
-   Risolvere conflitti in base alla priorità impostata.  
  
 La maggior parte dei Sottoscrittori non necessita di questa funzionalità ed è in grado di utilizzare una sottoscrizione client. Le sottoscrizioni client consentono ancora il rilevamento e la risoluzione dei conflitti, ma ai Sottoscrittori non viene assegnata una priorità. In altre parole, il primo Sottoscrittore che inoltra una modifica al server di pubblicazione prevale nei conflitti eventualmente generati da tale modifica.  
  
> [!NOTE]  
>  Dopo aver creato la sottoscrizione non è possibile modificarne il tipo.  
  
## Opzioni  
 **Proprietà sottoscrizione**  
 Per ogni server di sottoscrizione, selezionare **Client** o **Server** dalla casella di riepilogo a discesa il **tipo di sottoscrizione** colonna. Per i sottoscrittori con sottoscrizioni server, immettere un numero compreso tra 0 e 99,99 nella **priorità per la risoluzione dei conflitti** colonna (maggiore è il numero, maggiore è la priorità per il sottoscrittore).  
  
## Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  