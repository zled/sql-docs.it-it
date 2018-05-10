---
title: Restrizione della Query con Query e un asse di sezionamento (MDX) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c19bdf8b4850add274875fbe9af305d56a0aef4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-query-and-slicer-axes---restricting-the-query"></a>Query MDX e assi di sezionamento - restrizione della Query
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Per la formulazione di un'istruzione SELECT di MDX (Multidimensional Expression), un'applicazione in genere analizza il cubo e suddivide il set di gerarchie in due subset:  
  
-   **Assi della query**, ovvero il set di gerarchie da cui vengono recuperati i dati per più membri. Per altre informazioni sugli assi delle query, vedere [Impostazione del contenuto di un asse della query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md).  
  
-   **Asse di sezionamento**, ovvero il set di gerarchie da cui vengono recuperati i dati per un unico membro. Per altre informazioni sull'asse di sezionamento, vedere [Impostazione del contenuto di un asse di sezionamento &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md).  
  
 Poiché gli assi della query e di sezionamento possono essere costruiti da più gerarchie del cubo su cui eseguire la query, questi termini vengono utilizzati per distinguere le gerarchie utilizzate dal cubo su cui eseguire la query dalle gerarchie create nel cubo restituito da una query MDX.  
  
 Per vedere un semplice esempio di uso degli assi delle query e degli assi di sezionamento, vedere [Utilizzo di assi di query e assi di sezionamento in un semplice esempio &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di membri, tuple e set & #40; MDX & #41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Nozioni fondamentali sulle Query MDX & #40; Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
