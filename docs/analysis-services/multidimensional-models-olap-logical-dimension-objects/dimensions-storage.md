---
title: Dimensione di archiviazione | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 33720e0dc129d3effc872e06fa0240cf12a12721
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="dimensions---storage"></a>Dimensioni di archiviazione:
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dimensioni [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supportano due modalità di archiviazione:  
  
-   OLAP relazionale (ROLAP)  
  
-   OLAP multidimensionale (MOLAP)  
  
 La modalità di archiviazione determina la posizione e la forma dei dati di una dimensione. MOLAP è la modalità di archiviazione predefinita per le dimensioni. **Argomenti correlati:**[l'elaborazione e modalità di archiviazione delle partizioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
## <a name="molap"></a>MOLAP  
 I dati per una dimensione che utilizza la modalità MOLAP vengono archiviati in una struttura multidimensionale nell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tale struttura multidimensionale viene creata e popolata durante l'elaborazione della dimensione. Le dimensioni MOLAP garantiscono prestazioni di esecuzione delle query migliori rispetto alle dimensioni ROLAP.  
  
## <a name="rolap"></a>ROLAP  
 I dati per una dimensione che utilizza la modalità ROLAP vengono effettivamente archiviati nelle tabelle utilizzate per definire la dimensione. La modalità ROLAP può essere utilizzata per supportare dimensioni grandi senza duplicare quantità di dati elevate, a spese, però, delle prestazioni di esecuzione delle query. Poiché la dimensione si basa direttamente sulle tabelle della vista origine dati utilizzata per definire la dimensione, la modalità di archiviazione ROLAP supporta inoltre l'elaborazione OLAP in tempo reale.  
  
> [!IMPORTANT]  
>  Se una dimensione utilizza la modalità di archiviazione ROLAP ed è inclusa in un cubo che utilizza l'archiviazione MOLAP, qualsiasi modifica dello schema nella tabella di origine deve essere seguita dall'immediata elaborazione della dimensione. In caso contrario, i risultati delle query eseguite sui cubi potrebbero essere inconsistenti. **Argomento correlato:**[automatizzare Analysis Services attività amministrative con SSIS](../../analysis-services/instances/automate-analysis-services-administrative-tasks-with-ssis.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elaborazione e modalità di archiviazione di partizioni](../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-partition-storage-modes-and-processing.md)  
  
  
