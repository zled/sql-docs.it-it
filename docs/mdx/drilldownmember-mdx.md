---
title: DrilldownMember (MDX) | Documenti Microsoft
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
- DRILLDOWNMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownMember function
ms.assetid: 765f2fc7-0baa-428b-864a-22c9f3113083
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 05187989fb551e43bbf089c5944c9330f04dad11
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="drilldownmember-mdx"></a>DrilldownMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue il drill-down dei membri di un set specificato presenti in un secondo set specificato.  
  
 La funzione esegue in alternativa il drill-down su un set di tuple utilizzando la prima gerarchia di tuple o la gerarchia specificata facoltativamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DrillDownMember(<Set_Expression1>, <Set_Expression2> [,[<Target_Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Target_Hierarchy*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Ricorsivo*  
 Una parola chiave che indica il confronto ricorsivo tra set.  
  
 *Include_Calc_Members*  
 Una parola chiave per consentire l'inclusione dei membri calcolati nei risultati del drill-down.  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione restituisce un set di membri figlio ordinati in base alla gerarchia e comprende i membri specificati nel primo set che sono presenti anche nel secondo set. Il drill-down non verrà eseguito sui membri padre se il primo set contiene il membro padre e uno o più figli. Il primo set può avere qualsiasi dimensionalità, mentre il secondo deve contenere un set unidimensionale. L'ordine originale dei membri nel primo set viene mantenuto, con la sola differenza che nel set di risultati della funzione tutti i membri figlio vengono indicati immediatamente sotto il membro padre corrispondente. La funzione ottiene il set di risultati recuperando il membro figlio di ogni membro del primo set presente anche nel secondo set. Se **RICORSIVA** è specificato, la funzione continua in modo ricorsivo i membri del set di risultati con il secondo set, recuperare gli elementi figlio per ogni membro nel risultato set che di confronto presente anche nel secondo set fino a quando non più membri del set di risultati sono reperibile nel secondo set.  
  
 Query sulla proprietà XMLA **MdpropMdxDrillFunctions** consente di verificare il livello di supporto che il server garantisce per le funzioni di drill; vedere [proprietà XMLA supportate &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md)per informazioni dettagliate.  
  
 Il primo set può contenere tuple anziché membri. La funzione per il drill-down di tuple è un'estensione di OLE DB e restituisce un set di tuple anziché di membri.  
  
> [!IMPORTANT]  
>  Il drill-down di un membro non verrà eseguito se tale membro è immediatamente seguito da uno dei relativi figli. L'ordine dei membri nel set è rilevante per * drill-down e drill-up\* famiglie di funzioni.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eseguito il drill-down nel membro Australia del primo set, presente anche nel secondo set.  
  
```  
SELECT DrilldownMember   
   ( [Geography].[Geography].Children,  
      {[Geography].[Geography].[Country].[Australia],  
        [Geography].[Geography].[State-Province].[New South Wales]}  
   )  
   ON 0  
   FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene eseguito il drill-down nel membro Australia del primo set, presente anche nel secondo set. Poiché tuttavia è specificato l'argomento RECURSIVE, la funzione confronta ricorsivamente i membri del set di risultati, ovvero i membri del livello State-Province, con i membri del secondo set e recupera il membro figlio di ogni membro del set di risultati (i membri del livello City) presente anche nel secondo set fino a quando nel secondo set non viene individuato alcun membro del set di risultati.  
  
```  
SELECT DrilldownMember   
   ( [Geography].[Geography].Children,  
      {[Geography].[Geography].[Country].[Australia],  
        [Geography].[Geography].[State-Province].[New South Wales]}  
   ,RECURSIVE)  
   ON 0  
   FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
