---
title: "Contenuto di FORE_COLOR e BACK_COLOR (MDX) | Microsoft Docs"
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
  - "contenuto di FORE_COLOR"
  - "sfondi [MDX]"
  - "celle [MDX]"
  - "colori [MDX]"
  - "archiviazione di informazioni sui colori delle celle"
  - "sfondi di celle"
  - "contenuto di BACK_COLOR"
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Contenuto di FORE_COLOR e BACK_COLOR (MDX)
  Nelle proprietà **FORE_COLOR** e **BACK_COLOR** di una cella sono archiviate, rispettivamente, informazioni sui colori del testo e dello sfondo della cella, nel formato RGB di Microsoft Windows.  
  
 I valori validi per i colori RGB standard sono compresi tra zero (0) e 16.777.215 (&H00FFFFFF). Il primo byte di un numero in questo intervallo è sempre uguale a 0. I 3 byte successivi, dal meno significativo al più significativo, determinano rispettivamente le quantità di rosso, verde e blu. Ognuno dei componenti rosso, verde e blu è rappresentato da un numero compreso tra 0 e 255 (&HFF).  
  
## Vedere anche  
 [Uso delle proprietà delle celle &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-cell-properties-mdx.md)  
  
  