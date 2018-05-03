---
title: Istruzione CALL (MDX) | Documenti Microsoft
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
- CALL
dev_langs:
- kbMDX
helpviewer_keywords:
- voids [MDX]
- stored procedures [MDX]
- CALL statement
ms.assetid: b534a20b-924c-43b8-832d-24e57d50425c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 2f2614b552fe5b5f96dcb50dcd0bc85c857540b1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-manipulation---call"></a>Manipolazione dei dati MDX - chiamata
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue una stored procedure che restituisce un valore void nell'ambito corrente o facoltativamente in un cubo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CALL SP_Name   
   [ (SP_Argument   
      [, SP_Argument ,...n]  
      ) ]   
[ONCube_Expression]  
```  
  
## <a name="arguments"></a>Argomenti  
 *SP_Name*  
 Espressione stringa valida che specifica il nome di una stored procedure.  
  
 *SP_Argument*  
 Espressione stringa valida che specifica un argomento per la stored procedure chiamata.  
  
 *Cube_Expression*  
 Stringa espressione di cubo valida che specifica il nome del cubo.  
  
## <a name="remarks"></a>Osservazioni  
 Il **CHIAMARE** istruzione viene eseguita una stored procedure registrata specificata, includendo, facoltativamente, uno o più argomenti per la stored procedure specificata. Il **CHIAMARE** istruzione può essere utilizzata solo con stored procedure che restituiscono void. Questa istruzione non può essere combinata con altre funzioni o altri operatori in un'espressione MDX. Le stored procedure registrate che restituiscono valori possono essere chiamate direttamente all'interno delle espressioni MDX e combinate con altre funzioni e altri operatori MDX.  
  
 Se non viene specificato un cubo, l'istruzione esegue la stored procedure sul cubo corrente.  
  
> [!NOTE]  
>  Se la stored procedure non è registrata nel client, il **CHIAMARE** istruzione tenta di chiamare la stored procedure da un'istanza di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni MDX di manipolazione dei dati &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Uso di stored procedure &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
