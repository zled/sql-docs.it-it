---
title: "Rilevamento modifiche (Master Data Services) | Microsoft Docs"
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
  - "rilevamento delle modifiche [SQL Server]"
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Rilevamento modifiche (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]è possibile utilizzare gruppi rilevamento delle modifiche per eseguire un'azione quando cambia un valore di attributo. Utilizzare il rilevamento modifiche quando non si conosce il nuovo valore, ma si desidera sapere se sono state apportate modifiche.  
  
## Configurazione del rilevamento modifiche  
 Per configurare il rilevamento modifiche, aggiungere un attributo a un gruppo rilevamento modifiche. Il gruppo può contenere uno o molti attributi. Creare quindi una regola business per definire l'azione da eseguire quando uno degli attributi del gruppo vengono modificati.  
  
> [!NOTE]  
>  Le regole business del rilevamento modifiche considerano i dati in gestione temporanea (importati) come modificati.  
  
## Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Aggiungere attributi a un gruppo rilevamento modifiche.|[Aggiungere attributi ad un gruppo rilevamento modifiche &#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|Creare una regola business per avviare azioni in base alle modifiche apportate agli attributi.|[Inizializzare azioni basate su modifiche dei valori di attributo &#40;Master Data Services&#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## Contenuto correlato  
  
-   [Convalida &#40;Master Data Services&#41;](../master-data-services/validation-master-data-services.md)  
  
-   [Regole di business &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [Attributi &#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  