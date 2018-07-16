---
title: Definire automaticamente un nuovo attributo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- automatic attribute creation
- attributes [Analysis Services], creating
ms.assetid: 208a050a-5e2f-470c-b645-8d835e123db7
caps.latest.revision: 33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74b4e1950e6a31675994b7cae1562ff92a56de4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299191"
---
# <a name="define-a-new-attribute-automatically"></a>Definire automaticamente un nuovo attributo
  È possibile creare un nuovo attributo in una dimensione utilizzando la funzionalità di modifica tramite trascinamento in Progettazione dimensioni.  
  
### <a name="to-create-a-new-attribute-automatically"></a>Per creare un nuovo attributo automaticamente  
  
1.  In Progettazione dimensioni aprire la dimensione in cui si desidera creare l'attributo.  
  
2.  Nella scheda **Struttura dimensione** selezionare la colonna di una tabella nel riquadro **Vista origine dati** alla quale si vuole associare l'attributo e quindi trascinare la colonna nel riquadro **Attributi** .  
  
     [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] crea il nuovo attributo che ha lo stesso nome della colonna alla quale è associato. Se a una stessa colonna sono associati più attributi, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aggiunge un numero al nome dell'attributo.  
  
## <a name="see-also"></a>Vedere anche  
 [Dimensioni nei modelli multidimensionali](dimensions-in-multidimensional-models.md)   
 [Riferimento alle proprietà degli attributi delle dimensioni](dimension-attribute-properties-reference.md)  
  
  
