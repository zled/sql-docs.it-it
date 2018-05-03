---
title: Espressioni (MDX) | Documenti Microsoft
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
dev_langs:
- kbMDX
helpviewer_keywords:
- identifiers [MDX]
- expressions [MDX]
- expressions [MDX], about expressions
- MDX [Analysis Services], expressions
- Multidimensional Expressions [Analysis Services], expressions
ms.assetid: e20c34bc-30fa-4ac5-b896-9d4c9925ef59
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a158bbcdd77e4a7e1e026db793b46e306d8c6fbe
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="expressions-mdx"></a>Espressioni (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Un'espressione è una combinazione di identificatori, valori e operatori che [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] può valutare per ottenere un risultato. Nelle operazioni di accesso o modifica dei dati, è possibile utilizzare i dati in varie posizioni. Le espressioni possono essere utilizzate, ad esempio, come parte dei dati da recuperare tramite una query oppure come condizione per la ricerca di dati che soddisfano un set di criteri.  
  
## <a name="simple-and-complex-expressions"></a>Espressioni semplici o complesse  
 Un'espressione MDX può essere semplice o complessa:  
  
 Sono considerati semplici i tipi di espressioni seguenti:  
  
 Costante  
 In MDX una costante è un simbolo che rappresenta un singolo valore di dati specifico. Le costanti possono rappresentare valori stringa, numerici e di data. A differenza delle costanti numeriche, le costanti costituite da valori stringa e di data devono essere delimitate da virgolette singole (').  
  
 Funzioni scalari  
 In MDX una funzione scalare restituisce un singolo valore nel contesto di valutazione. Questa distinzione è importante per comprendere come vengono risolte le funzioni scalari in MDX, perché la maggior parte delle espressioni, delle istruzioni e degli script MDX non viene valutata su un singolo elemento di dati, ma iterativamente su un gruppo di elementi di dati quali celle o membri. Al momento della valutazione, tuttavia, la funzione scalare sta in genere esaminando un singolo elemento di dati.  
  
 Identificatori di oggetto  
 MDX è un linguaggio orientato a oggetti, a causa della natura dei dati multidimensionali. In MDX gli identificatori degli oggetti sono considerati espressioni semplici. Per ulteriori informazioni sugli identificatori, vedere [identificatori &#40;MDX&#41;](../mdx/identifiers-mdx.md).  
  
 Un'espressione complessa può essere compilata da combinazioni di queste entità unite tramite vari operatori.  
  
## <a name="expression-results"></a>Risultati dell'espressione  
 Per una semplice espressione compilata da un'unica costante, variabile, funzione scalare o nome di colonna, il tipo di dati, le regole di confronto, la precisione, la scala e il valore dell'espressione coincidono con quelli dell'elemento a cui viene fatto riferimento. Poiché MDX supporta direttamente solo il tipo di dati OLE VARIANT, quando si utilizzano espressioni semplici non avviene alcuna coercizione.  
  
 Per le espressioni complesse è possibile che venga applicata una coercizione quando si utilizzano due o più espressioni semplici con tipi di dati diversi.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 Nella query seguente vengono illustrati esempi di misure calcolate le cui definizioni sono espressioni semplici:  
  
 `WITH`  
  
 `MEMBER MEASURES.CONSTANTVALUE AS 1`  
  
 `MEMBER MEASURES.SCALARFUNCTION AS [Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.OBJECTIDENTIFIER AS [Measures].[Internet Sales Amount]`  
  
 `SELECT {MEASURES.CONSTANTVALUE,MEASURES.SCALARFUNCTION,MEASURES.OBJECTIDENTIFIER } ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 Un'espressione può essere anche costituita da un calcolo, ad esempio `[Measures].[Discount Amount] * 1.5`. Nell'esempio seguente viene illustrato l'utilizzo di un calcolo per la definizione di un membro in un'istruzione MDX SELECT:  
  
```  
WITH   
   MEMBER [Measures].[Special Discount] AS  
   [Measures].[Discount Amount] * 1.5  
SELECT   
   [Measures].[Special Discount] on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Uso di espressioni di cubo e sottocubo](../mdx/using-cube-and-subcube-expressions.md)|Definisce le espressioni di cubo e sottocubo.|  
|[Uso delle espressioni di dimensione](../mdx/using-dimension-expressions.md)|Definisce le espressioni di dimensione.|  
|[Uso delle espressioni di membro](../mdx/using-member-expressions.md)|Definisce le espressioni di membro.|  
|[Uso delle espressioni di tupla](../mdx/using-tuple-expressions.md)|Definisce le espressioni di tupla.|  
|[Uso di espressioni set](../mdx/using-set-expressions.md)|Definisce le espressioni set.|  
|[Uso di espressioni scalari](../mdx/using-scalar-expressions.md)|Definisce le espressioni scalari.|  
|[Uso di valori vuoti](../mdx/working-with-empty-values.md)|Illustra il concetto di valore vuoto e la modalità di gestione dei valori di questo tipo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti al linguaggio MDX & #40; MDX & #41;](../mdx/mdx-language-reference-mdx.md)   
 [Nozioni fondamentali sulle Query MDX & #40; Analysis Services & #41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
