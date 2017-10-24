---
title: Creare gerarchie definite dall'utente | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51e4bcb074da0b11587d8783008fd250fa8867fe
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="user-defined-hierarchies---create"></a>Creare gerarchie definite dall'utente-
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di creare gerarchie definite dall'utente. Una gerarchia è una raccolta di livelli basata su attributi. Ad esempio, la gerarchia temporale potrebbe includere i livelli Anno, Trimestre, Mese, Settimana e Giorno. In alcune gerarchie, ogni attributo del membro comprende in modo univoco l'attributo del membro che si trova ad un livello superiore. A questo talvolta si fa riferimento come gerarchia naturale. Una gerarchia può essere utilizzata dagli utenti finali per esplorare i dati del cubo. Definire gerarchie utilizzando il riquadro Gerarchie di Progettazione Dimensioni in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Quando si crea una gerarchia definita dall'utente, è possibile che la gerarchia sia *incompleta*. In una gerarchia incompleta, il membro padre logico di almeno un membro non si trova nel livello immediatamente superiore rispetto al membro stesso. Se si ha una gerarchia incompleta, ci sono impostazioni che controllano se i membri mancanti sono visibili e come visualizzare i membri mancanti. Per altre informazioni, vedere [Gerarchie incomplete](../../analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md).  
  
> [!NOTE]  
>  Per altre informazioni su problemi di prestazioni legati alla progettazione e alla configurazione delle gerarchie definite dall'utente, vedere la [Guida alle prestazioni di SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà delle gerarchie definite dall'utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Proprietà del livello - gerarchie utente](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [Dimensioni padre-figlio](../../analysis-services/multidimensional-models/parent-child-dimension.md)  
  
  

