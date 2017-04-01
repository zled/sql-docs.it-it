---
title: "Visualizzare il codice XML per un progetto di Analysis Services (SSDT) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
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
  - "progetti [Analysis Services], visualizzazione del codice XML"
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Visualizzare il codice XML per un progetto di Analysis Services (SSDT)
  Quando si utilizza un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modalità progetto, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] viene creata una definizione XML per ogni oggetto all'interno della cartella di progetto. È possibile visualizzare il contenuto del file XML per ogni oggetto in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. È inoltre possibile modificare direttamente il file XML. Nella maggior parte delle circostanze, tuttavia, ciò non è consigliabile poiché le modifiche apportate potrebbero rendere il codice XML illeggibile per [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
> [!NOTE]  
>  Non è possibile visualizzare il codice XML per un intero progetto. Viene invece visualizzato il codice per ogni oggetto, per il quale esiste un file separato. L'unico modo per visualizzare il codice per un intero progetto consiste nel compilare il progetto e visualizzare il codice ASSL nel file \<nome progetto>.asdatabase.  
  
### Per visualizzare il codice XML per un oggetto  
  
1.  Aprire il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Fare clic con il pulsante destro del mouse sull'oggetto in Esplora soluzioni e quindi scegliere **Visualizza codice**.  
  
     In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] verrà visualizzato il codice XML per l'oggetto.  
  
## Vedere anche  
 [Compilare progetti di Analysis Services &#40;SSDT&#41;](../../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)  
  
  