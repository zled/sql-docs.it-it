---
title: Creazione con ambito sessione celle calcolate | Documenti Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c0953df9aa142ce6826e96a3715970d51ec15158
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-cell-calculations---session-scoped-calculated-cells"></a>Calcoli MDX di cella - celle calcolate con ambito sessione
    
> [!IMPORTANT]  
>  Questa sintassi è deprecata e deve essere sostituita da istruzioni MDX di assegnazione. Per altre informazioni sull'assegnazione, vedere [Script MDX di base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Per creare celle calcolate disponibili a tutte le query di una stessa sessione, è possibile usare l'istruzione [CREATE CELL CALCULATION](../../../mdx/mdx-data-definition-create-cell-calculation.md) oppure l'istruzione [ALTER CUBE](../../../mdx/mdx-data-definition-alter-cube.md). Entrambe le istruzioni restituiscono lo stesso risultato.  
  
## <a name="create-cell-calculation-syntax"></a>Sintassi di CREATE CELL CALCULATION  
  
> [!IMPORTANT]  
>  Questa sintassi è deprecata e deve essere sostituita da istruzioni MDX di assegnazione. Per altre informazioni sull'assegnazione, vedere [Script MDX di base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Per utilizzare l'istruzione CREATE CELL CALCULATION per definire una cella calcolata con ambito sessione, utilizzare la sintassi seguente:  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## <a name="alter-cube-syntax"></a>Sintassi di ALTER CUBE  
  
> [!IMPORTANT]  
>  Questa sintassi è deprecata e deve essere sostituita da istruzioni MDX di assegnazione. Per altre informazioni sull'assegnazione, vedere [Script MDX di base &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md).  
  
 Per utilizzare l'istruzione ALTER CUBE per definire una cella calcolata con ambito sessione, utilizzare la sintassi seguente:  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 Il valore `String_Expression` contiene un elenco di espressioni set MDX unidimensionali ortogonali, ognuna delle quali deve essere risolta in una delle categorie di set elencate nella tabella seguente.  
  
|Category|Description|  
|--------------|-----------------|  
|Set vuoto|Espressione set MDX che restituisce un set vuoto. In questo caso l'ambito della cella calcolata è costituito dall'intero cubo.|  
|Set con un singolo membro|Espressione set MDX che restituisce un singolo membro.|  
|Set di membri di un livello|Espressione set MDX che restituisce i membri di un singolo livello. Un esempio è la funzione MDX *Level_Expression*.**Members** . Per includere i membri calcolati, usare la funzione MDX *Level_Expression*.**AllMembers**.<br /><br /> Per altre informazioni, vedere [AllMembers &#40;MDX&#41;](../../../mdx/allmembers-mdx.md).|  
|Set di discendenti|Espressione set MDX che restituisce i discendenti di un membro specificato. Un esempio è la funzione MDX **Descendants**(*Member_Expression*, *Level_Expression*, *Desc_Flag*).<br /><br /> Per altre informazioni, vedere [Descendants &#40;MDX&#41;](../../../mdx/descendants-mdx.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di formule per il calcolo di celle in MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)  
  
  

