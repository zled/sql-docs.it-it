---
title: "Relazione di sincronizzazione delle entit&#224; (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bd627a2d-dc64-47e9-9a71-2d0ad04b4962
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Relazione di sincronizzazione delle entit&#224; (Master Data Services)
  La sincronizzazione delle entità è una sincronizzazione unidirezionale e ripetibile tra le versioni dell'entità. Consente di condividere i dati dell'entità tra i vari modelli. È possibile mantenere un'unica origine in un modello e riusare questi dati master in altri modelli. Ad esempio, è possibile archiviare i dati sullo stato per gli Stati Uniti in un'entità di modello e riusare i dati in altri modelli.  
  
 Con la sincronizzazione delle entità, è anche possibile eseguire una copia occasionale dei dati.  
  
 Tutti i membri foglia con attributi di file e in formato libero nell'entità di origine sono sincronizzati con l'entità di destinazione durante la sincronizzazione. In questo modo vengono creati, eliminati e modificati i membri e lo schema dell'entità.  
  
 Dopo aver stabilito una relazione di sincronizzazione, l'entità di destinazione può essere modificata solo dal processo di sincronizzazione. Una relazione di sincronizzazione può essere rimossa in qualsiasi momento per rendere modificabile l'entità di destinazione.  
  
## Vedere anche  
 [Creare ed eseguire una relazione di sincronizzazione delle entità &#40;Master Data Services&#41;](../master-data-services/create-and-execute-an-entity-sync-relationship-master-data-services.md)   
 [Modificare ed eliminare una relazione di sincronizzazione delle entità &#40;Master Data Services&#41;](../master-data-services/edit-and-delete-an-entity-sync-relationship-master-data-services.md)  
  
  