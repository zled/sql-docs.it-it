---
title: ToggleDrillState (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bcd09f9c7ea8be177112e2a70ef04380ebc00146
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582383"
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
  
 Query sulla proprietà XMLA MdpropMdxDrillFunctions consente di verificare il livello di supporto che il server garantisce per le funzioni di drill; vedere [proprietà XMLA supportate &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) per informazioni dettagliate.  
  
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
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
