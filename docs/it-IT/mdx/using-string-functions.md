---
title: Utilizzo di funzioni stringa | Documenti Microsoft
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
- string functions
ms.assetid: 962e820a-a1f9-49b5-90f0-a05261e6682b
caps.latest.revision: 24
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: bf114f9b706497512f10e3629e871ba64ecaaee9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-string-functions"></a>Utilizzo di funzioni stringa
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Nel linguaggio MDX (Multidimensional Expressions) è possibile utilizzare funzioni stringa su quasi tutti gli oggetti. Nelle stored procedure le funzioni stringa vengono utilizzate principalmente per convertire un oggetto in una rappresentazione stringa. Le funzioni stringa possono essere inoltre utilizzate per valutare un'espressione stringa su un oggetto per restituire un valore.  
  
 Le funzioni di stringa più diffuse sono **nome** e **Uniquename**. Queste funzioni restituiscono rispettivamente il nome e il nome univoco di un oggetto. Sono utilizzate soprattutto durante i calcoli di debug per individuare quale membro viene restituito da una funzione.  
  
## <a name="examples"></a>Esempi  
 Negli esempi di query seguenti viene illustrato l'utilizzo di queste funzioni:  
  
 `WITH`  
  
 `//Returns the name of the current Product on rows`  
  
 `MEMBER [Measures].[ProductName] AS [Product].[Product].CurrentMember.Name`  
  
 `//Returns the uniquename of the current Product on rows`  
  
 `MEMBER [Measures].[ProductUniqueName] AS [Product].[Product].CurrentMember.Uniquename`  
  
 `//Returns the name of the Product dimension`  
  
 `MEMBER [Measures].[ProductDimensionName] AS [Product].Name`  
  
 `SELECT  {[Measures].[ProductName],[Measures].[ProductUniqueName],[Measures].[ProductDimensionName]}`  
  
 `ON COLUMNS,`  
  
 `[Product].[Product].MEMBERS  ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Il **genera** funzione può essere utilizzata per eseguire una funzione di stringa per ogni membro di un set e concatenare i risultati. Può essere utile anche durante il debug di calcoli in quanto consente di visualizzare il contenuto di un set. Nell'esempio seguente viene illustrato questo tipo di utilizzo:  
  
 `WITH`  
  
 `//Returns the names of the current Product and its ancestors up to the All Member`  
  
 `MEMBER [Measures].[AncestorNames] AS`  
  
 `GENERATE(`  
  
 `ASCENDANTS([Product].[Product Categories].CurrentMember)`  
  
 `, [Product].[Product Categories].CurrentMember.Name, ", ")`  
  
 `SELECT`  
  
 `{[Measures].[AncestorNames]}`  
  
 `ON COLUMNS,`  
  
 `[Product].[Product Categories].MEMBERS  ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 Un altro gruppo di funzioni per i valori stringa molto diffuso è costituito dalle funzioni che consentono di eseguire il cast di una stringa che contiene il nome univoco di un oggetto o un'espressione che viene risolta nell'oggetto all'interno dell'oggetto stesso. Query di esempio seguente viene illustrato come la **StrToMember** e **StrToSet** funzioni:  
  
 `SELECT`  
  
 `{StrToMember("[Measures].[Inter" + "net Sales Amount]")}`  
  
 `ON COLUMNS,`  
  
 `StrToSet("{`  
  
 `[Product].[Product Categories].[Category].&[3],`  
  
 `[Product].[Product Categories].[Product].&[477],`  
  
 `[Product].[Product Categories].[Product].&[788],`  
  
 `[Product].[Product Categories].[Product].&[708],`  
  
 `[Product].[Product Categories].[Product].&[711]`  
  
 `}")`  
  
 `ON ROWS`  
  
 `FROM [Adventure Works]`  
  
> [!NOTE]  
>  Il **StrToMember** e **StrToSet** funzioni devono essere utilizzate con cautela. in quanto, se utilizzate all'interno di definizioni di calcoli, possono ridurre drasticamente le prestazioni delle query.  
  
## <a name="see-also"></a>Vedere anche  
 [Genera &#40;MDX&#41;](../mdx/generate-mdx.md)   
 [Nome &#40;MDX&#41;](../mdx/name-mdx.md)   
 [UniqueName &#40;MDX&#41;](../mdx/uniquename-mdx.md)   
 [Le funzioni &#40;sintassi MDX&#41;](../mdx/functions-mdx-syntax.md)   
 [Utilizzo di Stored procedure &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)   
 [StrToMember &#40;MDX&#41;](../mdx/strtomember-mdx.md)   
 [StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md)  
  
  
