---
title: "Convalida sottoscrizione | Microsoft Docs"
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
  - "sql13.rep.validate.validateandresynch.f1"
helpviewer_keywords: 
  - "Convalida sottoscrizione - finestra di dialogo"
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Convalida sottoscrizione
  Utilizzare il **Convalida sottoscrizione** la finestra di dialogo per specificare che una sottoscrizione di una pubblicazione di tipo merge deve essere convalidata alla successiva esecuzione l'agente di Merge per la sottoscrizione. I risultati della convalida vengono visualizzati in Monitoraggio replica. Per altre informazioni, vedere [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
 È inoltre possibile convalidare tutte le sottoscrizioni di una pubblicazione di tipo merge facendo clic su una pubblicazione in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e facendo clic su **convalida tutte le sottoscrizioni**.  
  
## Opzioni  
 **Data ultimo tentativo di convalida**  
 Data dell'ultima sessione dell'agente di merge che prevedeva la convalida della sottoscrizione, indipendentemente dal fatto che la convalida sia stata completata o meno.  
  
 **Data ultima convalida**  
 Data dell'ultima sessione dell'agente di merge che prevedeva una convalida della sottoscrizione completata.  
  
 **Convalida la sottoscrizione**  
 Selezionare questa opzione per convalidare la sottoscrizione.  
  
 **Opzioni**  
 Fare clic su accesso il **le opzioni di convalida sottoscrizione** nella finestra di dialogo che consente di specificare se utilizzare la convalida mediante conteggio delle righe o convalida mediante checksum binario.  
  
## Vedere anche  
 [Convalida dei dati replicati](../../relational-databases/replication/validate-replicated-data.md)  
  
  