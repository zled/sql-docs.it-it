---
title: Gli elementi della sintassi MDX (MultiDimensional Expression) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], syntax
- MDX [Analysis Services], syntax
ms.assetid: f4c16e1a-cf1a-4be0-839a-db018430ff14
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 77aab8ddf130fc7f93cecfe762833bbda873c81a
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-syntax-elements-mdx"></a>Elementi della sintassi MDX (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il linguaggio MDX (Multidimensional Expressions) include numerosi elementi utilizzati nella maggior parte delle istruzioni o che ne influenzano l'esecuzione:  
  
|Nome|Definizione|  
|----------|----------------|  
|[Identificatori](../mdx/identifiers-mdx.md)|Gli identificatori sono nomi di oggetti quali cubi, dimensioni, membri e misure.|  
|**Tipi di dati**|Definiscono i tipi dei dati contenuti nelle celle, nelle proprietà dei membri e nelle proprietà delle celle. MDX supporta solo il tipo di dati OLE VARIANT. Per ulteriori informazioni sulla coercizione, la conversione e la modifica del tipo di dati VARIANT, vedere l'argomento dedicato a VARIANT e VARIANTARG nella documentazione di Platform SDK.|  
|[Espressioni &#40; MDX &#41;](../mdx/expressions-mdx.md)|Le espressioni sono unità di sintassi che [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] può restituire singoli valori (scalari) o oggetti. Le espressioni includono funzioni che restituiscono un singolo valore, un'espressione set e così via.|  
|[Operatori](../mdx/operators-mdx-syntax.md)|Gli operatori sono elementi di sintassi che utilizzano una o più espressioni MDX semplici per formare espressioni MDX più complesse.|  
|[Funzioni](../mdx/functions-mdx-syntax.md)|Le funzioni sono elementi di sintassi che accettano zero, uno o più valori di input e che restituiscono un valore scalare o un oggetto. Gli esempi includono la [somma](../mdx/sum-mdx.md) funzione per l'aggiunta di più valori, il [membri](../mdx/members-set-mdx.md) funzione per la restituzione di un set di membri da una dimensione o un livello e così via.|  
|[Commenti](../mdx/comments-mdx-syntax.md)|I commenti sono parti di testo inserite all'interno di istruzioni MDX o script per spiegarne lo scopo dell'istruzione. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]non esegue commenti.|  
|[Parole chiave riservate](../mdx/reserved-keywords-mdx-syntax.md)|Le parole chiave riservate sono parole che vengono utilizzate da MDX e non possono essere utilizzate come nomi per gli oggetti impiegati nelle istruzioni MDX.|  
|[I membri, tuple e set](../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)|Prima di creare una query MDX, è necessario comprendere i concetti di membro, tupla e set.|  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni MDX &#40; MDX &#41; Riferimento](../mdx/multidimensional-expressions-mdx-reference.md)  
  
  
