---
title: Utilizzo di Query e assi di sezionamento in un semplice esempio (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e27b8a961e692a9b1757573e4c735949fc537153
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="mdx-query-and-slicer-axes---using-axes-in-a-simple-example"></a>Query MDX e assi di sezionamento - mediante gli assi in un semplice esempio
  Il semplice esempio presentato in questo argomento illustra le nozioni fondamentali sull'impostazione e l'utilizzo di assi di query e assi di sezionamento.  
  
## <a name="the-cube"></a>Il cubo  
 Viene utilizzato un cubo con il nome TestCube e due semplici dimensioni, Route e Time. Ogni dimensione include un'unica gerarchia utente, Route e Time rispettivamente. Poiché le misure del cubo fanno parte della dimensione Measures, il cubo ha in tutto tre dimensioni.  
  
## <a name="the-query"></a>La query  
 La query deve restituire una matrice in cui è possibile confrontare la misura Packages su vari canali di distribuzione e periodi di tempo.  
  
 Nella seguente query MDX di esempio gli assi della query sono costituiti dalle gerarchie Route e Time, mentre la dimensione Measures costituisce l'asse di sezionamento. La funzione [Members](../../../mdx/members-set-mdx.md) indica che MDX utilizzerà i membri della gerarchia o del livello per costruire un set. Poiché viene utilizzata la funzione **Members** , non è necessario definire esplicitamente ogni membro di una gerarchia o di un livello specifico in una query MDX.  
  
```  
SELECT  
   { Route.nonground.Members } ON COLUMNS,  
   { Time.[1st half].Members } ON ROWS  
FROM TestCube  
WHERE ( [Measures].[Packages] )  
```  
  
## <a name="the-results"></a>I risultati  
 Il risultato è costituito da una griglia che identifica il valore della misura Packages per ogni intersezione delle dimensioni degli assi COLUMNS e ROWS. Tale griglia è illustrata nella tabella seguente.  
  
||air|sea|  
|-|---------|---------|  
|1st quarter|60|50|  
|2nd quarter|45|45|  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazione del contenuto di un asse della query &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)   
 [Impostazione del contenuto di un asse di sezionamento &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
