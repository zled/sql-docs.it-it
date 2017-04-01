---
title: "Riattivare un membro o una raccolta (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "04/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "raccolte [Master Data Services], riattivazione"
  - "membri consolidati [Master Data Services], riattivazione"
  - "riattivazione di membri [Master Data Services]"
  - "membri [Master Data Services], riattivazione"
  - "riattivazione di raccolte [Master Data Services]"
  - "membri foglia [Master Data Services], riattivazione"
ms.assetid: bb4884c0-3658-4763-92d1-636804278b1c
caps.latest.revision: 11
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 11
---
# Riattivare un membro o una raccolta (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] è possibile riattivare un membro che è stato:  
  
-   Disattivato dal processo di gestione temporanea.  
  
-   Eliminato in [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] MDS.  
  
-   Eliminato nell'applicazione Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
 Quando si riattiva un membro, i relativi attributi e l'appartenenza a gerarchie e raccolte vengono ripristinati.  
  
 È inoltre possibile riattivare le raccolte. Quando si esegue questa operazione, vengono ripristinati gli attributi della raccolta e i membri che appartengono ad essa.  
  
 Quando si riattiva una raccolta o un membro, vengono ripristinate tutte le transazioni precedenti.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] è necessario disporre dell'autorizzazione per l'area funzionale **Gestione versioni**.  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Per riattivare un membro o una raccolta  
  
1.  Scegliere **Gestione versioni** dalla home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
2.  Sulla barra dei menu fare clic su **Transazioni**.  
  
3.  Nella pagina **Transazioni** selezionare un modello dall'elenco **Modello**.  
  
4.  Selezionare una versione dall'elenco **Versione** .  
  
5.  Nel riquadro **Transazioni** fare clic sulla riga del membro o della raccolta che si vuole riattivare. Per questa riga deve essere visualizzata l'indicazione **Attivo** nella colonna **Valore precedente** e l'indicazione **Disattivato** nella colonna **Nuovo valore**.  
  
6.  Fare clic su **Inverti transazione selezionata**.  
  
7.  Nella finestra di dialogo di conferma fare clic su **OK**. Viene aggiunta una nuova transazione con l'indicazione **Attivo** nella colonna **Nuovo valore**.  
  
## Vedere anche  
 [Eliminare un membro o una raccolta &#40;Master Data Services&#41;](../master-data-services/delete-a-member-or-collection-master-data-services.md)   
 [Membri &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Raccolte &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
  