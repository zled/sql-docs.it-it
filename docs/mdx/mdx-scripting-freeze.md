---
title: Istruzione FREEZE (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9b7eb3a3939ce8525dc57d27a24ac005ecb2cf2d
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579903"
---
# <a name="mdx-scripting---freeze"></a>Creazione di script MDX - blocca
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Blocca sui valori correnti i valori delle celle del sottocubo specificato. Se vengono bloccati, i valori delle celle non subiscono gli effetti delle modifiche apportate ad altre celle.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FREEZE Subcube_Expression   
```  
  
## <a name="arguments"></a>Argomenti  
 *Subcube_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un sottocubo.  
  
## <a name="remarks"></a>Remarks  
 Il **bloccare** istruzione blocca i valori delle celle del sottocubo specificato, impedendo le successive istruzioni MDX passa script di modificare i valori nel calcolo successivo.  
  
 Nell'esempio seguente A e B rappresentano sottocubi in uno script di calcolo MDX:  
  
```  
B = 2;  
A = B;  
B = 3  
```  
  
 A questo punto, sia A che B sono uguali a 3.  
  
 Viene ora inserita la **bloccare** funzione per bloccare le celle nel sottocubo A:  
  
```  
B = 2;  
A = B;  
FREEZE(A);  
B = 3  
```  
  
 Ora A è uguale a 2 e B è uguale a 3.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni di Scripting MDX &#40;MDX&#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
