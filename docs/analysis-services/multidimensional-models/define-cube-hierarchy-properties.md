---
title: "Definire le propriet&#224; della gerarchia del cubo | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "gerarchie [Analysis Services], multilivello"
  - "gerarchie [Analysis Services], cubi"
ms.assetid: 819d0a4e-7815-4332-a605-b07ca2ade6ac
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 18
---
# Definire le propriet&#224; della gerarchia del cubo
  Le proprietà delle gerarchie dei cubi consentono di specificare impostazioni univoche per gerarchie definite dall'utente in dimensioni del cubo basate sulla stessa dimensione del database. Nella tabella seguente vengono descritte le proprietà della gerarchia di un cubo.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Abilitata**|Determina l'eventuale abilitazione della gerarchia per la dimensione del cubo.|  
|**HierarchyID**|Contiene l'identificatore univoco (ID) della gerarchia.|  
|**OptimizedState**|Determina il livello di ottimizzazione applicato alla gerarchia. I possibili valori della proprietà sono i seguenti:<br /><br /> **FullyOptimized**:<br />                    L'istanza compila indici per la gerarchia allo scopo di migliorare le prestazioni di esecuzione delle query. Si tratta del valore predefinito.<br /><br /> **NotOptimized**:<br />                    L'istanza non compila indici aggiuntivi.|  
|**Visible**|Determina la visibilità della gerarchia del cubo. Il valore predefinito è **True**.|  
  
## Vedere anche  
 [Gerarchie definite dall'utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  