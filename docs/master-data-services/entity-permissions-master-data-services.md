---
title: "Autorizzazioni per le entit&#224; (Master Data Services) | Microsoft Docs"
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
  - "entità [Master Data Services], autorizzazioni"
  - "autorizzazioni [Master Data Services], entità"
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Autorizzazioni per le entit&#224; (Master Data Services)
  Le autorizzazioni per le entità si applicano a:  
  
-   Tutti gli attributi dell'entità, inclusi **Name** e **Code**, per i membri foglia e i membri consolidati.  
  
-   Tutte le raccolte dell'entità.  
  
-   Appartenenze e relazioni della gerarchia esplicita.  
  
 Quando si dispone delle autorizzazioni per un'entità, è possibile aggiungere e rimuovere membri dall'entità, dalle gerarchie esplicite e dalle raccolte corrispondenti.  
  
> [!NOTE]  
>  Queste autorizzazioni si applicano solo all'area funzionale **Visualizzatore** dell'interfaccia utente.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Lettura**|L'utente può leggere i membri, gli attributi, le appartenenze a gerarchie o le appartenenze a raccolte.|  
|**Create**|L'utente può creare i membri e assegnare i valori di attributo durante la creazione.|  
|**Update**|L'utente può aggiornare i membri, gli attributi, le appartenenze a gerarchie o le appartenenze a raccolte.|  
|**Elimina**|L'utente può eliminare i membri.|  
|**Nega**|Nega ogni accesso all'entità.|  
  
 Le autorizzazioni di lettura, creazione, aggiornamento ed eliminazione possono essere combinate. Quando vengono assegnate le autorizzazioni di creazione, aggiornamento ed eliminazione, l'autorizzazione di lettura viene assegnata automaticamente.  
  
## Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Entità &#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  