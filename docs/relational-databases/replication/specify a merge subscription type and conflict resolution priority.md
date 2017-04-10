---
title: "Impostazione di una sottoscrizione di tipo merge e della priorit&#224; per la risoluzione dei conflitti (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "risoluzione dei conflitti di replica di tipo merge [replica di SQL Server], sistemi di risoluzione di sottoscrizioni di tipo merge"
  - "risoluzione dei conflitti [replica di SQL Server], replica di tipo merge"
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Impostazione di una sottoscrizione di tipo merge e della priorit&#224; per la risoluzione dei conflitti (SQL Server Management Studio)
  Specificare un merge sottoscrizione tipo e il conflitto di priorità per la risoluzione sul **tipo di sottoscrizione** pagina della procedura guidata nuova sottoscrizione. Per ulteriori informazioni sull'utilizzo di questa procedura guidata, vedere [creare una sottoscrizione Pull](../../relational-databases/replication/create-a-pull-subscription.md) e [creare una sottoscrizione Push](../../relational-databases/replication/create-a-push-subscription.md).  
  
 Tipo di sottoscrizione non può essere modificato dopo che viene creata una sottoscrizione, ma è possibile modificare la priorità per il tipo di sottoscrizione server nella **Proprietà sottoscrizione - \< Publisher>: \< PublicationDatabase>** la finestra di dialogo. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md) e [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md).  
  
### Per specificare una sottoscrizione di tipo merge e la priorità per la risoluzione dei conflitti  
  
1.  Nel **tipo di sottoscrizione** pagina della creazione guidata sottoscrizione, selezionare **Client** o **Server** per il **tipo di sottoscrizione** (opzione).  
  
2.  Se si seleziona un tipo di sottoscrizione **Server**, immettere anche un valore (compreso tra 0,00 e 99,99) per il **priorità per la risoluzione dei conflitti** (opzione).  
  
### Per modificare la priorità per la risoluzione dei conflitti  
  
1.  Nel **Proprietà sottoscrizione - \< Publisher>: \< PublicationDatabase>** nel server di pubblicazione, immettere un valore (compreso tra 0,00 e 99,99) per il **priorità** (opzione).  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Vedere anche  
 [Rilevamento e risoluzione avanzati dei conflitti nella replica di tipo merge](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  