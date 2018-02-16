---
title: Contenuto di FORE_COLOR e Back_color (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 921f3bb6b8d8458d534ecd629aa6eba52fe704ae
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="mdx-cell-properties---forecolor-and-backcolor-contents"></a>Proprietà di cella MDX - contenuto di FORE_COLOR e Back_color
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Nelle proprietà **FORE_COLOR** e **BACK_COLOR** di una cella sono archiviate, rispettivamente, informazioni sui colori del testo e dello sfondo della cella, nel formato RGB di Microsoft Windows.  
  
 I valori validi per i colori RGB standard sono compresi tra zero (0) e 16.777.215 (&H00FFFFFF). Il primo byte di un numero in questo intervallo è sempre uguale a 0. I 3 byte successivi, dal meno significativo al più significativo, determinano rispettivamente le quantità di rosso, verde e blu. Ognuno dei componenti rosso, verde e blu è rappresentato da un numero compreso tra 0 e 255 (&HFF).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzando le proprietà della cella &#40; MDX &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)  
  
  
