---
title: "Autorizzazioni per elementi foglia (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gruppi di attributi [Master Data Services], autorizzazioni"
  - "membri [Master Data Services], autorizzazioni per membri foglia"
  - "autorizzazioni [Master Data Services], membri foglia"
  - "membri foglia [Master Data Services], autorizzazioni per attributi"
  - "attributi [Master Data Services], autorizzazioni per attributi membri foglia"
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
caps.latest.revision: 9
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# Autorizzazioni per elementi foglia (Master Data Services)
  Le autorizzazioni foglia si applicano ai valori di attributo per tutti i membri foglia di un'entità.  
  
 Per le entità senza gerarchie esplicite abilitate, l'assegnazione delle autorizzazioni all'elemento **Foglia** equivale all'assegnazione delle autorizzazioni all'entità.  
  
 **Note:**  
  
-   Le autorizzazioni foglia si applicano solo all'area funzionale **Visualizzatore** dell'interfaccia utente.  
  
-   Le autorizzazioni assegnate agli attributi **Name** e **Code** non sono applicate.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Lettura**|L'utente può leggere i membri foglia e i relativi attributi.|  
|**Create**|L'utente può creare i membri foglia e assegnare i valori di attributo durante la creazione.|  
|**Update**|L'utente può aggiornare i membri foglia e gli attributi.|  
|**Elimina**|L'utente può eliminare i membri foglia.|  
|**Nega**|Negare l'accesso ai membri foglia.|  
  
 Le autorizzazioni di lettura, creazione, aggiornamento ed eliminazione possono essere combinate. Quando vengono assegnate le autorizzazioni di creazione, aggiornamento ed eliminazione, l'autorizzazione di lettura viene assegnata automaticamente.  
  
## Autorizzazioni per attributi  
 Le autorizzazioni per gli attributi si applicano ai valori degli attributi per l'entità specifica. Gli utenti che dispongono solo delle autorizzazioni per gli attributi non possono aggiungere o rimuovere membri.  
  
|Autorizzazione|Description|  
|----------------|-----------------|  
|**Lettura**|L'utente può leggere gli attributi.|  
|**Crea**|L'utente può assegnare valori durante la creazione di membri.|  
|**Update**|L'utente può aggiornare gli attributi.|  
|**Elimina**|Nessun effetto.|  
|**Nega**|L'attributo non viene visualizzato.<br /><br /> Nota: non è possibile negare in modo esplicito l'accesso agli attributi Name e Code.|  
  
### Esempio  
 Per l'entità Product, assegnare l'autorizzazione **Update** all'attributo Subcategory. Negare l'autorizzazione per tutti gli altri attributi.  
  
|Nome|Codice|Subcategory (Aggiornamento)|  
|----------|----------|----------------------------|  
|Mountain-100|BK-M101|{5} Mountain Bikes|  
|Mountain-100|BK-M201|{5} Mountain Bikes|  
  
 Nel **Visualizzatore** è possibile aggiornare qualsiasi valore di attributo nella colonna Subcategory. Se non si dispone delle autorizzazioni per un attributo, l'attributo non viene visualizzato.  
  
> [!NOTE]  
>  In questo esempio, Subcategory è un attributo basato su dominio, basato sull'entità SubcategoryList. È possibile selezionare una sottocategoria diversa per Mountain-100, ma non è possibile aggiungere o eliminare membri dall'entità SubcategoryList.  
  
## Vedere anche  
 [Assegnare autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Autorizzazioni consolidate &#40;Master Data Services&#41;](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)   
 [Autorizzazioni per oggetti modello &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Membri &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Attributi &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  