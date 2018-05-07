---
title: DrilldownLevelBottom (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DRILLDOWNLEVELBOTTOM
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownLevelBottom function
ms.assetid: c00a6a02-e618-4713-805a-870e042f2d51
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: bea453215ad4c44ba697af9945b10447ee73dcc5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="drilldownlevelbottom-mdx"></a>DrilldownLevelBottom (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue il drill-down, fino al livello immediatamente inferiore, dei membri di livello più basso di un set al livello specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
DrilldownLevelBottom(Set_Expression, Count [,[<Level_Expression>] [,[<Numeric_Expression>][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Count*  
 Espressione numerica valida che specifica il numero di tuple che devono essere restituite.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Numeric_expression*  
 Facoltativa. Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
 *Include_Calc_Members*  
 Facoltativa. Parola chiave che consente di aggiungere i membri calcolati ai risultati del drill-down.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificata un'espressione numerica, la **DrilldownLevelBottom** funzione dispone in ordine crescente, gli elementi figlio di ogni membro nel set specificato, in base al valore specificato, valutato sul set di membri figlio. Se non è specificata un'espressione numerica, la funzione dispone in ordine crescente membri figlio di ciascun membro nel set specificato, in base ai valori delle celle rappresentate dal set di membri figlio, determinato dal contesto di query. Questo comportamento è simile alle funzioni BottomCount e Tail (MDX) che restituiscono un set di membri in ordine naturale, senza alcun ordinamento.  
  
 Dopo l'ordinamento, il **DrilldownLevelBottom** funzione restituisce un set che contiene i membri padre e il numero di membri figlio, specificato in *conteggio*, con il valore più basso.  
  
 Il **DrilldownLevelBottom** è simile alla funzione di [DrilldownLevel](../mdx/drilldownlevel-mdx.md) funzione, ma anziché includere tutti gli elementi figlio per ogni membro al livello specificato, il **DrilldownLevelBottom** funzione restituisce il numero più basso di membri figlio.  
  
 Query sulla proprietà XMLA MdpropMdxDrillFunctions consente di verificare il livello di supporto che il server garantisce per le funzioni di drill; vedere [proprietà XMLA supportate &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) per informazioni dettagliate.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti gli ultimi tre membri figlio del livello Product Category in base alla misura predefinita. Nel cubo di esempio Adventure Works gli ultimi tre membri figlio per Accessories sono Tires and Tubes, Pumps e Panniers. Nella finestra Query MDX di Management Studio è possibile passare a Products | Product Categories | Members | All Products | Accessories per visualizzare l'elenco completo. È possibile incrementare l'argomento Count per restituire più membri.  
  
```  
SELECT DrilldownLevelBottom   
   ([Product].[Product Categories].children,  
   3,  
   [Product].[Product Categories].[Category])  
   ON 0  
   FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene illustrato l'utilizzo di **include_calc_members** flag, per includere i membri calcolati di drill-down livello. La misura [Reseller Order Count] viene aggiunta per il **DrilldownLevelBottom** istruzione per assicurarsi che i risultati vengono ordinati in base a tale misura. Per visualizzare il membro calcolato, è necessario incrementare Count almeno a 9.  
  
```  
WITH MEMBER   
[Product].[Product Categories].[Category].&[3].[Premium Clothes] AS  
[Product].[Product Categories].[Subcategory].&[18] +  
[Product].[Product Categories].[Subcategory].&[21]  
SELECT [Measures].[Reseller Order Count] ON 0,  
DRILLDOWNLEVELBOTTOM(  
  [Product].[Product Categories].children ,  
  9,  
  [Product].[Product Categories].[Category] ,  
  [Measures].[Reseller Order Count],  
  INCLUDE_CALC_MEMBERS ) ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DrilldownLevel & #40; MDX & #41;](../mdx/drilldownlevel-mdx.md)   
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
