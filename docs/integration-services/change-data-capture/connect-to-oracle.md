---
title: "Connettersi a Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "connOra"
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
caps.latest.revision: 5
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 5
---
# Connettersi a Oracle
  Quando si aggiungono o modificano le tabelle utilizzate nell'istanza di CDC per la prima volta, è possibile che venga richiesto di connettersi al database Oracle. Immettere le credenziali di un utente Oracle che può accedere allo schema delle tabelle da acquisire. Immettere quanto segue nella finestra di dialogo:  
  
 **Autenticazione**  
  
 Selezionare una delle opzioni seguenti:  
  
-   **Windows Authentication**: selezionare questa opzione per utilizzare le credenziali del dominio Windows correnti. È possibile utilizzare questa opzione solo se il database Oracle è configurato per l'utilizzo dell'autenticazione di Windows.  
  
-   **Oracle Authentication**: se si seleziona questa opzione, è necessario digitare il **nome utente** e la **password** dell'utente nel database Oracle a cui si effettua la connessione.  
  
## Vedere anche  
 [Aggiungere tabelle a un'istanza di CDC](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)  
  
  