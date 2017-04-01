---
title: "Aggiungere attributi ad un gruppo rilevamento modifiche (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gruppi rilevamento modifiche [Master Data Services]"
  - "attributi [Master Data Services], gruppi rilevamento modifiche"
  - "gruppi rilevamento modifiche [Master Data Services], aggiunta di attributi"
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Aggiungere attributi ad un gruppo rilevamento modifiche (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] aggiungere attributi a un gruppo rilevamento modifiche quando si vuole tenere traccia delle modifiche apportate ai valori dell'attributo.  
  
> [!NOTE]  
>  In seguito all'aggiunta di un attributo a un gruppo rilevamento modifiche, quando si modificano i valori relativi a tale attributo, l'attributo viene contrassegnato nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Creare una regola business per eseguire le azioni appropriate in base alla modifica.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   È necessario che esistano degli attributi da aggiungere al gruppo rilevamento modifiche. Per altre informazioni, vedere [Creare un attributo di testo &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md).  
  
### Per aggiungere attributi ad un gruppo rilevamento modifiche  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Nella pagina **Gestisci modelli** selezionare un modello dalla griglia, quindi fare clic su **Entità**.  
  
3.  Nella pagina **Gestisci entità** selezionare la riga dell'entità per la quale si vuole creare un attributo.  
  
4.  Fare clic su **Attributi**.  
  
5.  Nella pagina **Gestisci attributi** eseguire una delle operazioni seguenti.  
  
    -   Se l'attributo è per i membri foglia, selezionare **Foglia** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per i membri consolidati, selezionare **Consolidato** nella casella di riepilogo **Tipo di membro** .  
  
    -   Se l'attributo è per le raccolte, selezionare **Raccolta** nella casella di riepilogo **Tipo di membro** .  
  
6.  Selezionare la riga per l'attributo che si vuole modificare e quindi fare clic su **Modifica**.  
  
7.  Selezionare la casella di controllo **Abilita rilevamento modifiche**.  
  
8.  Nella casella **Gruppo rilevamento modifiche** digitare un numero per il gruppo.  
  
9. Fare clic su **Salva attributo**.  
  
     Per l'attributo modificato, la colonna del gruppo **Abilita rilevamento modifiche** nella griglia viene modificata in **Sì (gruppo: numero del gruppo immesso)**.  
  
10. Ripetere questa procedura per tutti gli attributi che si desidera includere nel gruppo. Utilizzare lo stesso numero del gruppo rilevamento modifiche per ciascun attributo del gruppo.  
  
## Passaggi successivi  
  
-   [Inizializzare azioni basate su modifiche dei valori di attributo &#40;Master Data Services&#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## Vedere anche  
 [Creare un attributo di testo &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Creare un attributo basato su dominio &#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  