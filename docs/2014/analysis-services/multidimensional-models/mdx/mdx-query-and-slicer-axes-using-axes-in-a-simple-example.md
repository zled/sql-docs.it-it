---
title: Utilizzo di Query e assi di sezionamento in un semplice esempio (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- slicer axis
- query axis [MDX]
ms.assetid: 85bcb26f-5971-4153-b334-61f8d8b475b5
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0be467a75ed63c91e97b7fcd9aeef2e59944f09b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170231"
---
# <a name="using-query-and-slicer-axes-in-a-simple-example-mdx"></a>Utilizzo di assi di query e assi di sezionamento in un semplice esempio (MDX)
  Il semplice esempio presentato in questo argomento illustra le nozioni fondamentali sull'impostazione e l'utilizzo di assi di query e assi di sezionamento.  
  
## <a name="the-cube"></a>Il cubo  
 Viene utilizzato un cubo con il nome TestCube e due semplici dimensioni, Route e Time. Ogni dimensione include un'unica gerarchia utente, Route e Time rispettivamente. Poiché le misure del cubo fanno parte della dimensione Measures, il cubo ha in tutto tre dimensioni.  
  
## <a name="the-query"></a>La query  
 La query deve restituire una matrice in cui è possibile confrontare la misura Packages su vari canali di distribuzione e periodi di tempo.  
  
 Nella seguente query MDX di esempio gli assi della query sono costituiti dalle gerarchie Route e Time, mentre la dimensione Measures costituisce l'asse di sezionamento. La funzione [Members](/sql/mdx/members-set-mdx) indica che MDX utilizzerà i membri della gerarchia o del livello per costruire un set. Poiché viene utilizzata la funzione `Members`, non è necessario definire esplicitamente ogni membro di una gerarchia o di un livello specifico in una query MDX.  
  
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
 [Impostazione del contenuto di un asse della Query &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)   
 [Impostazione del contenuto di un asse di sezionamento &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
