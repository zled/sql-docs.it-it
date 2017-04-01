---
title: "Assegnare un flag a una versione (Master Data Services) | Microsoft Docs"
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
  - "flag di versione [Master Data Services], assegnazione di flag"
  - "versioni [Master Data Services], assegnazione di flag"
ms.assetid: 6629ec7e-32e7-4a1e-8b31-eb43c5923766
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Assegnare un flag a una versione (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] assegnare un flag a una versione per indicare la versione che utenti o sistemi di sottoscrizione devono utilizzare.  
  
> [!NOTE]  
>  I flag di versione possono essere solo assegnati a una versione alla volta. Se si assegna un flag già assegnato a un'altra versione, il flag verrà spostato alla versione che si è selezionata.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale **Gestione versioni**.  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   È necessario aver creato un flag di versione da assegnare. Per altre informazioni, vedere [Creare un flag di versione &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md).  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale Gestione versioni. Per altre informazioni, vedere [Autorizzazioni per aree funzionali &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### Per assegnare un flag a una versione  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Gestione versioni**.  
  
2.  Nella pagina **Gestisci versioni** nella riga per la versione a cui si vuole assegnare un flag, fare doppio clic sulla cella nella colonna **Flag**.  
  
3.  Nell'elenco selezionare il flag che si desidera assegnare.  
  
    > [!NOTE]  
    >  Se il flag desiderato non è disponibile, è possibile che sia disponibile solo per le versioni con **Commit completato**. Per confermare, passare alla pagina **Gestisci flag di versione** e visualizzare il campo **Solo versioni con commit** per il flag.  
  
4.  Premere INVIO per salvare la modifica la formula.  
  
## Vedere anche  
 [Creare un flag di versione &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md)   
 [Versioni &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)  
  
  