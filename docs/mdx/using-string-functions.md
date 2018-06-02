---
title: Utilizzo di funzioni stringa | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 464bbe4ad20085571103a64f48716773c8352dea
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581753"
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
  
  
