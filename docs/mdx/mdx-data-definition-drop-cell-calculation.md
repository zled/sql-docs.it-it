---
title: Istruzione DROP CELL CALCULATION (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Calculation
- DROP
- DROP_CELL_CALCULATION
- CELL CALCULATION
- DROP CELL
- cell
- DROP CELL CALCULATION
dev_langs: kbMDX
helpviewer_keywords:
- deleting calculations
- dropping calculations
- removing calculations
- DROP CELL CALCULATION statement
- calculations [SQL Server]
- cubes [Analysis Services], calculations
ms.assetid: 77caedf4-dd96-4eac-a5e4-fd82148a44a7
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3b6eb5761f8f9036c4585b4ac81860f676759388
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-definition---drop-cell-calculation"></a>Definizione dei dati MDX - DROP CELL CALCULATION
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [CREARE l'istruzione di calcolo di celle &#40; MDX &#41;](../mdx/mdx-data-definition-create-cell-calculation.md)   
 [Le istruzioni di definizione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
