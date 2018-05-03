---
title: Contenuto di FORE_COLOR e Back_color (MDX) | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7071d143a5d9adb4e30817bd35c1f6aca0b4d5a2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-cell-properties---forecolor-and-backcolor-contents"></a>Proprietà di cella MDX - contenuto di FORE_COLOR e Back_color
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Nelle proprietà **FORE_COLOR** e **BACK_COLOR** di una cella sono archiviate, rispettivamente, informazioni sui colori del testo e dello sfondo della cella, nel formato RGB di Microsoft Windows.  
  
 I valori validi per i colori RGB standard sono compresi tra zero (0) e 16.777.215 (&H00FFFFFF). Il primo byte di un numero in questo intervallo è sempre uguale a 0. I 3 byte successivi, dal meno significativo al più significativo, determinano rispettivamente le quantità di rosso, verde e blu. Ognuno dei componenti rosso, verde e blu è rappresentato da un numero compreso tra 0 e 255 (&HFF).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzando le proprietà della cella & #40; MDX & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)  
  
  
