---
title: Errore (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6644318053321ae5189a70a2bd2c1f0e67d092fc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740710"
---
# <a name="error-mdx"></a>Error (MDX)


  Genera un errore, visualizzando facoltativamente il messaggio di errore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Error( [ Error_Text ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Error_Text*  
 Espressione stringa valida contenente il messaggio di errore da restituire.  
  
## <a name="examples"></a>Esempi  
 La query seguente viene illustrato come utilizzare il **errore** funzione all'interno di una misura calcolata:  
  
 `WITH MEMBER MEASURES.ERRORDEMO AS ERROR("THIS IS AN ERROR")`  
  
 `SELECT`  
  
 `MEASURES.ERRORDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
