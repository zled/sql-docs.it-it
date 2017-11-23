---
title: Predecessori (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ASCENDANTS
dev_langs: kbMDX
helpviewer_keywords: Ascendants function
ms.assetid: a2baf4a2-7d66-4766-b708-739a3c21b09e
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 2b81f8dffc10d5fa62c264814d3f1215c7f44c5a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il set dei predecessori del membro specificato, incluso il membro stesso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Il **predecessori** funzione restituisce tutti i predecessori di un membro del membro nella parte superiore della gerarchia del membro; in particolare, esegue un attraversamento post-ordine della gerarchia per il membro specificato e restituisce tutti i predecessori correlati al membro, incluso se stesso, in un set. È in contrasto con la [predecessore](../mdx/ancestor-mdx.md) funzione che restituisce un membro di predecessori specifico o predecessore, a un livello specifico.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce il numero di ordini dei rivenditori per il `[Sales Territory].[Northwest]` membro e tutti i predecessori di tale membro dal **Adventure Works** cubo. Il **predecessori** funzione costruisce il set che include il `[Sales Territory].[Northwest]` membro e i relativi predecessori per l'asse ROWS.  
  
```  
SELECT  
   Measures.[Reseller Order Count] ON COLUMNS,  
   Order(  
      Ascendants(  
         [Sales Territory].[Northwest]  
      ),  
      DESC  
   ) ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
