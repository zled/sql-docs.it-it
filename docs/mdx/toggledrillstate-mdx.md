---
title: ToggleDrillState (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: TOGGLEDRILLSTATE
dev_langs: kbMDX
helpviewer_keywords: ToggleDrillState function
ms.assetid: 26fa1a0d-3ed1-45dc-955d-0591d49e4db9
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e8564128db3f9eaa06e7eb5bfe93880c74c5b3b3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="toggledrillstate-mdx"></a>ToggleDrillState (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Alterna lo stato di drill dei membri tra le modalità di drill-down e drill-up.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ToggleDrillState(Set_Expression1,Set_Expression2 [, [RECURSIVE] [,INCLUDE_CALC_MEMBERS] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Ricorsivo*  
 (Facoltativo) Una parola chiave che indica il confronto ricorsivo tra set. Il **ToggleDrillState** funzione è una combinazione del **DrillupMember** e **DrilldownMember** funzioni. La ricorsione si applica solo quando il membro è incluso il **DrilldownMember** stato.  
  
 *Include_calc_members*  
 (Facoltativo) Flag che indica se includere i membri calcolati, se presenti, al livello di drill-down.  
  
## <a name="remarks"></a>Remarks  
 Il **ToggleDrillState** funzione attiva/disattiva lo stato di drill di ogni membro del secondo set presente nel primo set. Il primo set può contenere tuple con qualsiasi dimensionalità, mentre il secondo deve contenere membri di una sola dimensione. Il **ToggleDrillState** funzione è una combinazione del **DrillupMember** e **DrilldownMember** funzioni. Se il membro, *m*del secondo set è presente nel primo set e tale membro è drill-down (ovvero, ha un discendente che lo segue immediatamente), quindi `DrillupMember(Set_Expression1, {m})` viene applicato al membro o una tupla nel primo set. Se tale *m* membro è stato eseguito backup (che significa che non vi è alcun discendente di *m* che seguono immediatamente *m*), `DrilldownMember(Set_Expression1, {m}[, RECURSIVE])` viene applicato al primo set.  
  
 Se l'opzione facoltativa **RICORSIVA** flag viene utilizzato, drill-up e drill-down vengono applicate in modo ricorsivo. Per ulteriori informazioni sul flag recursive, vedere il [DrillupMember](../mdx/drillupmember-mdx.md) e [DrilldownMember](../mdx/drilldownmember-mdx.md) funzioni.  
  
 Query sulla proprietà XMLA MdpropMdxDrillFunctions consente di verificare il livello di supporto forniti dal server per le funzioni di drill; vedere [supportate proprietà XMLA &#40; XMLA &#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) per informazioni dettagliate.  
  
 Vedere [Database Journal: funzioni Set MDX: la funzione ToggleDrillState](http://go.microsoft.com/fwlink/?LinkId=517759) per scenari ed esempi che includono questa funzione.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono eseguiti il drill-down del membro Australia e il drill-up del membro United States del primo set.  
  
```  
SELECT ToggleDrillState  
   ({[Geography].[Geography].[Country].Members, [Geography].[Geography].[Country].&[United States].Children},  
      {[Geography].[Geography].[Country].[Australia]  
      , [Geography].[Geography].[Country].&[United States]}  
      --, recursive  
      --, include_calc_members  
   ) ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
