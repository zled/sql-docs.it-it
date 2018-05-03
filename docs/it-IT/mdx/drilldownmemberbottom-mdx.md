---
title: DrilldownMemberBottom (MDX) | Documenti Microsoft
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
- DRILLDOWNMEMBERBOTTOM
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownMemberBottom function
ms.assetid: 603927ba-68f6-4e7a-b17f-44cad33bdfb0
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b740a78a8d8cd425587e568db4a7cae521ad78e9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="drilldownmemberbottom-mdx"></a>DrilldownMemberBottom (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue il drill-down dei membri di un set specificato presenti in un secondo set specificato, limitando il set di risultati al numero specificato di membri. Questa funzione esegue inoltre in alternativa il drill-down su un set di tuple utilizzando la prima gerarchia di tuple o la gerarchia specificata facoltativamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DrillDownMemberBottom(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expresion>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Count*  
 Espressione numerica valida che specifica il numero di tuple che devono essere restituite.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
 *Gerarchia*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Ricorsivo*  
 Una parola chiave che indica il confronto ricorsivo tra set.  
  
 *Include_Calc_Members*  
 Una parola chiave per consentire l'inclusione dei membri calcolati nei risultati del drill-down.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificata un'espressione numerica, la **DrilldownMemberBottom** funzione dispone in ordine crescente, gli elementi figlio di ogni membro nel primo set, in base al valore dell'espressione numerica, valutato sul set di membri figlio. Se non viene specificata un'espressione numerica, la funzione dispone in ordine crescente i membri figlio di ogni membro nel primo set in base ai valori delle celle rappresentate dal set di membri figlio, come determinato dal contesto della query. Questo comportamento è simile alle funzioni BottomCount e Tail (MDX) che restituiscono un set di membri in ordine naturale, senza alcun ordinamento.  
  
 Dopo l'ordinamento, il **DrilldownMemberBottom** funzione restituisce un set che contiene i membri padre e il numero di membri figlio, specificato in *conteggio,* con il valore più basso e sono contenute in entrambi i set.  
  
 Se **RICORSIVA** viene specificato, la funzione ordina il primo set come descritto in precedenza, quindi confronta in modo ricorsivo ai membri del primo set, organizzati in una gerarchia, con il secondo set. La funzione recupera il numero di membri figlio inferiore di ogni membro del primo set presente anche nel secondo.  
  
 Il primo set può contenere tuple anziché membri. La funzione per il drill-down di tuple è un'estensione di OLE DB e restituisce un set di tuple anziché di membri.  
  
 Il **DrilldownMemberBottom** è simile alla funzione di [DrilldownMember](../mdx/drilldownmember-mdx.md) funzione, ma anziché includere tutti gli elementi figlio per ogni membro nel primo set che è anche presente nel secondo set, il **DrilldownMemberBottom** funzione restituisce il numero inferiore di membri figlio per ogni membro.  
  
 Query sulla proprietà XMLA MdpropMdxDrillFunctions consente di verificare il livello di supporto che il server garantisce per le funzioni di drill; vedere [proprietà XMLA supportate &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) per informazioni dettagliate.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
