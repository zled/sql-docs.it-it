---
title: Istruzione DROP CELL CALCULATION (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ac37584d12f2efa68084ada626ba57ab9fb28155
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579313"
---
# <a name="mdx-data-definition---drop-cell-calculation"></a>Definizione dei dati MDX - DROP CELL CALCULATION
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Rimuove la formula per il calcolo di celle specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP [ SESSION ] CELL CALCULATION CURRENTCUBE | Cube_Name.CellCalc_Name  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Espressione stringa valida che specifica il nome di una espressione di cubo.  
  
 *CellCalc_Name*  
 Espressione stringa valida che specifica il nome della formula per il calcolo di celle da eliminare.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione CREATE CELL CALCULATION &#40;MDX&#41;](../mdx/mdx-data-definition-create-cell-calculation.md)   
 [Istruzioni di definizione dei dati MDX &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
