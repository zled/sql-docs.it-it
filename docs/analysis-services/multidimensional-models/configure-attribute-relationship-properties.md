---
title: "Configurare le propriet&#224; della relazione tra attributi | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
  - "relazioni flessibili (Analysis Services)"
  - "attributi [Analysis Services], relazioni"
  - "relazioni [Analysis Services], attributi"
  - "proprietà [Analysis Services], relazioni tra attributi"
  - "relazioni rigide (Analysis Services)"
ms.assetid: fce511af-66d7-42fc-bb3a-6c516f16b10e
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Configurare le propriet&#224; della relazione tra attributi
  Nella tabella seguente vengono elencate e descritte le proprietà di una relazione tra attributi.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|Attribute|Nome dell'attributo.|  
|Cardinalità|Indica la cardinalità della relazione. Il valore è Many per una relazione molti-a-uno e One per una relazione uno-a-uno. Il valore predefinito è Many. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] la proprietà Cardinality non ha alcun effetto. L'uso di tale proprietà è riservato per un'implementazione futura.|  
|Nome|Nome descrittivo dell'attributo.|  
|RelationshipType|Indica se le relazioni tra membri cambiano nel tempo. Il valore di questa proprietà è Rigid se le relazioni tra membri non cambiano nel tempo o Flexible in caso contrario. Il valore predefinito è Flexible. Se si definisce una relazione flessibile, le aggregazioni verranno eliminate e ricalcolate come parte di un aggiornamento incrementale. Non verranno invece eliminate se vengono aggiunti solo nuovi membri. Se viene definita una relazione rigida, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di mantenere le aggregazioni quando la dimensione viene aggiornata in modo incrementale. Se una relazione definita rigida viene modificata, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verrà generato un errore durante l'aggiornamento incrementale. L'impostazione corretta delle relazioni e delle rispettive proprietà determina un miglioramento delle prestazioni durante l'esecuzione di query e i processi di elaborazione.|  
|Visible|Determina la visibilità della relazione tra attributi. Il valore è True o False. Il valore predefinito è True.|  
  
  