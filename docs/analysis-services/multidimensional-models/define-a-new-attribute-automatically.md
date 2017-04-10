---
title: "Definire automaticamente un nuovo attributo | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creazione automatica di attributi"
  - "attributi [Analysis Services], creazione"
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Definire automaticamente un nuovo attributo
  È possibile creare un nuovo attributo in una dimensione utilizzando la funzionalità di modifica tramite trascinamento in Progettazione dimensioni.  
  
### Per creare un nuovo attributo automaticamente  
  
1.  In Progettazione dimensioni aprire la dimensione in cui si desidera creare l'attributo.  
  
2.  Nella scheda **Struttura dimensione** selezionare la colonna di una tabella nel riquadro **Vista origine dati** alla quale si vuole associare l'attributo e quindi trascinare la colonna nel riquadro **Attributi**.  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crea il nuovo attributo che ha lo stesso nome della colonna alla quale è associato. Se a una stessa colonna sono associati più attributi, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aggiunge un numero al nome dell'attributo.  
  
## Vedere anche  
 [Dimensioni nei modelli multidimensionali](../../analysis-services/multidimensional-models/dimensions-in-multidimensional-models.md)   
 [Riferimento alle proprietà degli attributi delle dimensioni](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  