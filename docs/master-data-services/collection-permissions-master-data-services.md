---
title: "Autorizzazioni per raccolte (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "raccolte [Master Data Services], autorizzazioni"
  - "autorizzazioni [Master Data Services], raccolte"
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Autorizzazioni per raccolte (Master Data Services)
  Le autorizzazioni per le raccolte si applicano a tutte le raccolte relative a un'entità. Non è possibile assegnare autorizzazioni a una raccolta specifica. Le autorizzazioni si applicano a tutte le raccolte.  
  
> [!NOTE]  
>  Queste autorizzazioni si applicano solo all'area funzionale **Visualizzatore** dell'interfaccia utente.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Lettura**|L'utente può leggere i membri della raccolta e gli attributi dei membri.|  
|**Create**|L'utente può creare i membri della raccolta e assegnare i valori di attributo.|  
|**Update**|L'utente può aggiornare i membri della raccolta, gli attributi e le relazioni.|  
|**Elimina**|L'utente può eliminare membri della raccolta.|  
|**Nega**|L'accesso ai membri della raccolta è negato.|  
  
 Le autorizzazioni di lettura, creazione, aggiornamento ed eliminazione possono essere combinate. Quando vengono assegnate le autorizzazioni di creazione, aggiornamento ed eliminazione, l'autorizzazione di lettura viene assegnata automaticamente.  
  
## Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Raccolte &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  