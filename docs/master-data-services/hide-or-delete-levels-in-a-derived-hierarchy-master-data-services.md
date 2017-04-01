---
title: "Nascondere o eliminare livelli di una gerarchia derivata (Master Data Services) | Microsoft Docs"
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
  - "gerarchie derivate, livelli nascosti"
  - "gerarchie derivate, eliminazione di livelli"
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Nascondere o eliminare livelli di una gerarchia derivata (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] è possibile nascondere un livello di una gerarchia derivata quando è necessario per il raggruppamento ma non si vuole visualizzarlo. Eliminare un livello quando non si desidera utilizzarlo per il raggruppamento.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Per nascondere o eliminare i livelli di una gerarchia derivata  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Scegliere **Gestisci** dalla barra dei menu e fare clic su **Gerarchie derivate**.  
  
3.  Nella pagina **Gestione gerarchia derivata** dall'elenco **Modello** selezionare un modello.  
  
4.  Selezionare la riga relativa alla gerarchia derivata da modificare.  
  
5.  Fare clic su **Modifica**.  
  
6.  Nel riquadro **Livelli correnti**:  
  
    -   Per nascondere un livello, fare clic su un livello diverso quello superiore o inferiore. Nell'elenco **Visibile** selezionare **No**. Quindi fare clic su **Salva elemento gerarchia selezionato**.  
  
    -   Per eliminare il livello superiore, fare clic su **Elimina elemento gerarchia selezionato**. Nella finestra di dialogo di conferma fare clic su **OK**. È possibile eliminare solo il livello superiore.  
  
## Vedere anche  
 [Spostare membri all'interno di una gerarchia &#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)   
 [Gerarchie derivate &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  