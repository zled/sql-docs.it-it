---
title: "Gerarchie derivate con estremit&#224; esplicite (Master Data Services) | Microsoft Docs"
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
  - "gerarchie [Master Data Services], derivate con estremità esplicite"
  - "gerarchie esplicite, gerarchie derivate con estremità esplicite"
  - "gerarchie derivate, con estremità esplicite"
ms.assetid: 6a82ff66-c137-4757-99bb-787d189b4295
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Gerarchie derivate con estremit&#224; esplicite (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], quando i livelli di una gerarchia esplicita vengono usati come livelli principali di una gerarchia derivata, questa viene chiamata gerarchia derivata con estremità esplicita.  
  
 La gerarchia esplicita deve essere basata sulla stessa entità dell'entità al livello principale della gerarchia derivata.  
  
 Nell'interfaccia utente di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], si crea questo tipo di gerarchia trascinando una gerarchia esplicita al di sopra di una gerarchia derivata.  
  
 ![mds_conc_explicit_cap_UI_structure](../master-data-services/media/mds-conc-explicit-cap-ui-structure.gif "mds_conc_explicit_cap_UI_structure")  
  
## Esempio di gerarchia derivata con estremità esplicita  
 In questo esempio, i membri nella gerarchia esplicita provengono dall'entità Subcategory. Nella gerarchia derivata, anche i membri del livello principale provengono dall'entità Subcategory.  
  
 ![mds_conc_explicit_cap_UI_example](../master-data-services/media/mds-conc-explicit-cap-ui-example.gif "mds_conc_explicit_cap_UI_example")  
  
 Posizionando la gerarchia esplicita al di sopra di una gerarchia derivata, la gerarchia derivata diventa incompleta.  
  
## Regole  
  
-   Non è possibile avere più di una gerarchia esplicita in una gerarchia derivata con estremità esplicita.  
  
-   È possibile utilizzare come estremità la stessa gerarchia esplicita per più gerarchie derivate.  
  
-   Non è possibile assegnare autorizzazioni membri gerarchia alle gerarchie derivate con estremità esplicite. Se si assegnano autorizzazioni individualmente alla gerarchia esplicita o alla gerarchia derivata, le autorizzazioni hanno effetto su entrambe le gerarchie.  
  
## Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare una gerarchia derivata.|[Creare una gerarchia derivata &#40;Master Data Services&#41;](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|Creare una gerarchia esplicita.|[Creare una gerarchia esplicita &#40;Master Data Services&#41;](../master-data-services/create-an-explicit-hierarchy-master-data-services.md)|  
|Eliminare una gerarchia derivata esistente.|[Eliminare una gerarchia derivata &#40;Master Data Services&#41;](../master-data-services/delete-a-derived-hierarchy-master-data-services.md)|  
|||  
  
## Contenuto correlato  
  
-   [Gerarchie derivate &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
-   [Gerarchie esplicite &#40;Master Data Services&#41;](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
  