---
title: "Propriet&#224; database di distribuzione | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.distdbproperties.f1"
helpviewer_keywords: 
  - "Proprietà database di distribuzione - finestra di dialogo"
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Propriet&#224; database di distribuzione
  Il **proprietà Database di distribuzione** la finestra di dialogo consente di visualizzare un numero di proprietà e per impostare il periodo di memorizzazione delle transazioni e il periodo di memorizzazione cronologia per il database.  
  
## Opzioni  
 **Nome**  
 Il nome del database di distribuzione, il cui valore predefinito è "distribution" (sola lettura).  
  
 **Percorsi dei file**  
 Il percorso del file di database e del file di log (sola lettura).  
  
 **Periodo di memorizzazione della transazione**  
 Questa proprietà è nota anche come periodo di memorizzazione della distribuzione. Si tratta della quantità di tempo di memorizzazione delle transazioni ai fini della replica transazionale. Per altre informazioni, vedere [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Periodo di memorizzazione cronologia**  
 Quantità di tempo di memorizzazione dei metadati della cronologia ai fini di tutti i tipi di replica.  
  
 **Sicurezza agente di lettura coda**  
 L'agente di lettura coda viene utilizzato dalla replica transazionale con sottoscrizioni ad aggiornamento in coda. Un agente di lettura coda viene creato automaticamente se si seleziona **pubblicazione transazionale con sottoscrizioni aggiornabili** sul **tipo di pubblicazione** pagina della procedura guidata nuova pubblicazione. Fare clic su **le impostazioni di protezione...** Per modificare l'account con cui l'agente viene eseguito e stabilisce connessioni al server di distribuzione.  
  
 È inoltre possibile creare un agente di lettura coda selezionando **Crea agente di lettura coda** in questa pagina (questa opzione è disabilitata se l'agente è già stato creato).  
  
 Ulteriori informazioni sulla connessione relative all'agente di lettura coda vengono specificate in due posizioni:  
  
-   L'agente si connette al server di pubblicazione utilizzando le credenziali specificate nel **proprietà server di pubblicazione** la finestra di dialogo, disponibile tramite il **editori** pagina del **proprietà server di distribuzione** la finestra di dialogo.  
  
-   L'agente si connette al Sottoscrittore mediante le credenziali specificate per l'agente di distribuzione in Creazione guidata nuova sottoscrizione.  
  
 Per ulteriori informazioni, vedere  \\[modello di sicurezza dell'agente di replica](../Topic/Replication%20Agent%20Security%20Model.md).  
  
## Vedere anche  
 [Configurazione della distribuzione](../../relational-databases/replication/configure-distribution.md)   
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  