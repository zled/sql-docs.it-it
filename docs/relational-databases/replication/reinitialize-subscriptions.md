---
title: "Reinizializzare le sottoscrizioni | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "inizializzazione della sottoscrizioni [replica di SQL Server], reinizializzazione"
  - "sottoscrizioni [replica di SQL Server], reinizializzazione"
  - "reinizializzazione di sottoscrizioni"
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
caps.latest.revision: 51
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 51
---
# Reinizializzare le sottoscrizioni
  La reinizializzazione di una sottoscrizione consiste nell'applicare un nuovo snapshot di uno o più articoli a uno o più Sottoscrittori. Nella replica transazionale e snapshot è possibile reinizializzare singoli articoli, mentre nella replica di tipo merge è necessario reinizializzare tutti gli articoli. In una topologia di replica transazionale peer-to-peer non è possibile reinizializzare i nodi. Per verificare se un nodo dispone di una nuova copia dei dati, ripristinare un backup nel nodo stesso. La reinizializzazione avviene per uno dei due motivi seguenti:  
  
-   Una sottoscrizione viene contrassegnata esplicitamente per la reinizializzazione.  
  
-   Viene eseguita un'azione che richiede la reinizializzazione, ad esempio la modifica di una proprietà. Per ulteriori informazioni sulle azioni che richiedono la reinizializzazione, vedere [Modifica proprietà della pubblicazione e articolo](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 In entrambi i casi, alla successiva esecuzione dell'agente di distribuzione o dell'agente di merge, al Sottoscrittore viene applicato lo snapshot più recente. Nella replica snapshot e transazionale, al momento della reinizializzazione le modifiche apportate nel Sottoscrittore non ancora sincronizzate con il server di pubblicazione vengono sovrascritte dall'applicazione del nuovo snapshot.  
  
 Nella replica di tipo merge è possibile scegliere di caricare dal Sottoscrittore tutte le modifiche apportate ai dati prima di applicare lo snapshot. Tutte le modifiche dello schema in sospeso vengono applicate dal server di pubblicazione al Sottoscrittore e tutti gli aggiornamenti eseguiti nel Sottoscrittore dopo l'ultima sincronizzazione vengono distribuiti al server di pubblicazione prima di applicare nuovamente lo snapshot. Questo comportamento è controllato dal **upload_first** e **automatic_reinitialization_policy** proprietà; per ulteriori informazioni, vedere [reinizializzare una sottoscrizione](../../relational-databases/replication/reinitialize-a-subscription.md). Se si contrassegna una sottoscrizione per la reinizializzazione tramite SQL Server Management Studio o Monitoraggio replica, viene fornita un'opzione **Reinizializza sottoscrizioni** la finestra di dialogo per caricare innanzitutto le modifiche.  
  
> [!IMPORTANT]  
>  Se si aggiunge, elimina o modifica un filtro con parametri in una pubblicazione di tipo merge, non sarà possibile caricare le modifiche in sospeso dal Sottoscrittore al server di pubblicazione durante la reinizializzazione. Per caricare le modifiche in sospeso, sincronizzare tutte le sottoscrizioni prima di modificare il filtro.  
  
 Se durante la creazione della sottoscrizione è stata disattivata l'applicazione dello snapshot iniziale al Sottoscrittore e quindi si contrassegna la sottoscrizione per la reinizializzazione, non verrà applicato uno snapshot. Per ulteriori informazioni, vedere [inizializzare una sottoscrizione transazionale senza uno Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 **Per reinizializzare una sottoscrizione**  
  
 Per reinizializzare tutti gli articoli di una sottoscrizione, utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], stored procedure oppure oggetti RMO (Replication Management Objects). Per reinizializzare singoli articoli di pubblicazioni snapshot e transazionali, è necessario utilizzare stored procedure. Per ulteriori informazioni, vedere [reinizializzare una sottoscrizione](../../relational-databases/replication/reinitialize-a-subscription.md).  
  
## Vedere anche  
 [Inizializzazione di una sottoscrizione](../../relational-databases/replication/initialize-a-subscription.md)   
 [Scadenza e disattivazione delle sottoscrizioni](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  