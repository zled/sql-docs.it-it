---
title: Istruzione FREEZE (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- FREEZE
dev_langs:
- kbMDX
helpviewer_keywords:
- FREEZE statement
- locking cell values [MDX]
ms.assetid: 59f1e860-6f37-41af-97d6-7708bdaac933
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f122428b224f22dfd1899a77787ec86e65314280
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Osservazioni  
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
 [Istruzioni di Scripting MDX & #40; MDX & #41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
