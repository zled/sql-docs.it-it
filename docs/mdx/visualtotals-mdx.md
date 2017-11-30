---
title: VisualTotals (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VisualTotals
dev_langs: kbMDX
helpviewer_keywords: VisualTotals function
ms.assetid: 8ec529c2-729a-4a5b-892e-750849ab4013
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 892416035746861e0777b8d695a283231c2ddea5
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="visualtotals-mdx"></a>VisualTotals (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce un set generato calcolando dinamicamente il totale dei membri figlio in un set specificato, utilizzando facoltativamente un modello per il nome del membro padre nel set di risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
VisualTotals(Set_Expression[,Pattern])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Modello*  
 Espressione stringa valida per il membro padre del set, contenente un asterisco (*) come carattere di sostituzione per il nome del padre.  
  
## <a name="remarks"></a>Osservazioni  
 L'espressione set specificata può indicare un set contenente membri a qualsiasi livello in una singola dimensione, in genere membri con una relazione predecessore-discendente. Il **VisualTotals** funzione sommati i valori dei membri figlio nel set specificato e ignora i membri figlio non inclusi nel set nel calcolo dei totali del risultato. Vengono calcolati i totali visualizzati per i set ordinati nella gerarchia. Se l'ordine dei membri nei set viola la gerarchia, i risultati non costituiscono totali visualizzati. VisualTotals (USA, WA, CA, Seattle), ad esempio, non restituisce WA come Seattle, bensì restituisce i valori di WA, CA e Seattle e quindi calcola il totale di tali valori come totale visualizzato per USA, conteggiando due volte le vendite di Seattle.  
  
> [!NOTE]  
>  L'applicazione di **VisualTotals** funzione per i membri della dimensione che non sono correlati a una misura o sotto la granularità del gruppo di misure determinerà i valori verranno sostituiti con null.  
  
 *Modello*, che è facoltativo, specifica il formato per l'etichetta dei totali. *Modello* richiede un asterisco (*) come carattere di sostituzione per il membro padre e il resto del testo nella stringa viene visualizzato nel risultato come concatenato al nome del padre. Per visualizzare un asterisco letterale, utilizzare due asterischi (\*\*).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il totale visualizzato per il terzo trimestre dell'anno di calendario 2001 in base all'unico discendente specificato, ovvero il mese di luglio.  
  
```  
SELECT VisualTotals  
   ({[Date].[Calendar].[Calendar Quarter].&[2001]&[3]  
      ,[Date].[Calendar].[Month].&[2001]&[7]}) ON 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene restituito il membro [Totale] della gerarchia dell'attributo Category nella dimensione Product, con due dei quattro elementi figlio. Il totale restituito per il membro [Totale] per la misura Internet Sales Amount corrisponde al totale per i soli membri Accessories e Clothing. Viene inoltre utilizzato l'argomento Pattern per specificare l'etichetta per la colonna [All Products].  
  
```  
SELECT  
   VisualTotals  
   ({[Product].[Category].[All Products]  
      ,[Product].[Category].[Accessories]  
      ,[Product].[Category].[Clothing]}  
      , '* - Visual Total'  
   ) ON Columns  
, [Measures].[Internet Sales Amount] ON Rows  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
