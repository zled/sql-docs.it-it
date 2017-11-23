---
title: Istruzione SCOPE (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SCOPE
dev_langs: kbMDX
helpviewer_keywords:
- scope [MDX]
- SCOPE statement
ms.assetid: ceab459d-b601-4468-b3fc-4f5bb4a1805f
caps.latest.revision: "38"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: db7bf473a47753c64e050311d97c04e91c23cb39
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-scripting---scope"></a>Creazione di script MDX - ambito
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Limita l'ambito delle istruzioni MDX (Multidimensional Expression) specificate a un sottocubo specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SCOPE(Subcube_Expression)   
   [ MDX_Statement ]  
END SCOPE  
  
Subcube_Expression ::=(Auxiliary_Subcube [, Auxiliary_Subcube,...n])  
  
Auxiliary_Subcube ::=   
        Limited_Set   
    | Root([dimension_name])   
    | Leaves([dimension_name])  
  
Limited_Set ::=   
        single_tuple   
    | member   
    | Common_Grain_Members   
    | hierarchy.members   
    | level.members   
    | {}   
    | Descendants  
            (  
                  Member  
         , [level  
         [  
            , SELF   
             | AFTER   
                          | BEFORE   
                          | SELF_AND_AFTER   
                          | SELF_AND_BEFORE   
                          | SELF_BEFORE_AFTER   
                          | LEAVES  
                  ]  
            )   
[* <limited set>]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Subcube_Expression*  
 Espressione di sottocubo MDX valida.  
  
 *MDX_Statement*  
 Istruzione MDX valida.  
  
 *Common_Grain_Members*  
 Istruzione MDX valida che restituisce i membri allo stesso livello di dettaglio.  
  
 *single_tuple*  
 Una tupla singola.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione SCOPE determina il sottocubo che interessato dall'esecuzione di una o più istruzioni MDX. Se l'istruzione MDX non è racchiusa all'interno di un'istruzione SCOPE, il suo ambito implicito è l'intero cubo.  
  
> [!NOTE]  
>  In una istruzione SCOPE i membri nascosti vengono esposti.  
  
 Istruzioni SCOPE creano sottocubi che espongono "fori" indipendentemente la **MDX Compatibility** impostazione. L'istruzione `Scope( Customer.State.members )`, ad esempio, può includere gli stati per aree o paesi che non contengono stati ma al posto dei quali sono stati inseriti membri segnaposto altrimenti invisibili.  
  
 L'istruzione SCOPE non ha effetto sui membri calcolati e sui set denominati creati all'interno dell'istruzione SCOPE.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente, da script di calcolo MDX della soluzione di esempio Adventure Works, definisce l'ambito corrente come trimestre fiscale dell'anno fiscale 2005 e la misura di sales amount quota e quindi assegna un valore per le celle nell'ambito corrente utilizzando il **ParallelPeriod** (funzione). Nell'esempio viene quindi modificato l'ambito utilizzando un'altra istruzione SCOPE e quindi esegue un'altra assegnazione mediante il [This (MDX)](../mdx/this-mdx.md) (funzione).  
  
```  
Scope   
 (   
    [Date].[Fiscal Year].&[2005],  
    [Date].[Fiscal].[Fiscal Quarter].Members,  
    [Measures].[Sales Amount Quota]  
 ) ;     
  
   This = ParallelPeriod                               
          (   
             [Date].[Fiscal].[Fiscal Year], 1,  
             [Date].[Fiscal].CurrentMember   
          ) * 1.35 ;  
  
/*-- Allocate equally to months in FY 2002 -----------------------------*/  
  
  Scope   
  (   
     [Date].[Fiscal Year].&[2002],  
     [Date].[Fiscal].[Month].Members   
  ) ;     
  
    This = [Date].[Fiscal].CurrentMember.Parent / 3 ;     
  
  End Scope ;     
End Scope ;     
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni di Scripting MDX &#40; MDX &#41;](../mdx/mdx-scripting-statements-mdx.md)  
  
  
