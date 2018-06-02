---
title: Proprietà (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b564d11696999ec2dbd778d15a3e881cab415259
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581133"
---
# <a name="properties-mdx"></a>Properties (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce una stringa o un valore fortemente tipizzato contenente il valore delle proprietà di un membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Properties(Property_Name [, TYPED])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Property_name*  
 Espressione stringa valida del nome della proprietà di un membro.  
  
## <a name="remarks"></a>Remarks  
 Il **proprietà** funzione restituisce il valore del membro specificato per la proprietà di membro specificato. La proprietà del membro può essere ad esempio le proprietà intrinseche dei membri, **nome**, **ID**, **chiave**, o **DIDASCALIA**, oppure può essere una proprietà del membro definita dall'utente. Per altre informazioni, vedere [proprietà intrinseche dei membri &#40;MDX&#41; ](../analysis-services/multidimensional-models/mdx/mdx-member-properties-intrinsic-member-properties.md) e [proprietà dei membri definite dall'utente &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties-user-defined-member-properties.md).  
  
 Per impostazione predefinita, il valore è impostato forzatamente su una stringa. Se **TIPIZZATO** viene specificato, il valore restituito deve essere fortemente tipizzato.  
  
-   Se la proprietà è di tipo intrinseco, la funzione restituirà il tipo originale del membro.  
  
-   Se il tipo della proprietà è di tipo definito dall'utente, il tipo del valore restituito è identico al tipo del valore restituito del **MemberValue** (funzione).  
  
> [!NOTE]  
>  Properties ('Key') restituisce lo stesso risultato di Key0 ad eccezione delle chiavi composte. Per le chiavi composte Properties ('Key') restituirà Null. Usare la chiave*x* sintassi per le chiavi composte, come illustrato nell'esempio. Properties ('Key0'), Properties('Key1'), Properties('Key2') ecc formano la chiave composta.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituite le proprietà del membro intrinseche e definite dall'utente, utilizzando l'argomento TYPED per restituire il valore fortemente tipizzato per la proprietà del membro Day Name.  
  
```  
WITH MEMBER Measures.MemberName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Name')  
MEMBER Measures.MemberVal AS   
   [Date].[Calendar].[July 1, 2003].Properties('Member_Value')  
MEMBER Measures.MemberKey AS   
   [Date].[Calendar].[July 1, 2003].Properties('Key')  
MEMBER Measures.MemberID AS   
   [Date].[Calendar].[July 1, 2003].Properties('ID')  
MEMBER Measures.MemberCaption AS   
   [Date].[Calendar].[July 1, 2003].Properties('Caption')  
MEMBER Measures.DayName AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name', TYPED)  
MEMBER Measures.DayNameTyped AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day Name')  
MEMBER Measures.DayofWeek AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Week')  
MEMBER Measures.DayofMonth AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Month')  
MEMBER Measures.DayofYear AS   
   [Date].[Calendar].[July 1, 2003].Properties('Day of Year')  
  
SELECT {Measures.MemberName  
   , Measures.MemberVal  
   , Measures.MemberKey  
   , Measures.MemberID  
   , Measures.MemberCaption  
   , Measures.DayName  
   , Measures.DayNameTyped  
   , Measures.DayofWeek  
   , Measures.DayofMonth  
   , Measures.DayofYear  
   }  ON 0  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene illustrato come utilizzare la chiave*x* proprietà.  
  
```  
WITH   
MEMBER Measures.MemberKey AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key')  
MEMBER Measures.MemberKey0 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key0')  
MEMBER Measures.MemberKey1 AS   
   [Customer].[Customer Geography].[State-Province].&[QLD]&[AU].Properties('Key1')  
  
SELECT {Measures.MemberKey  
   , Measures.MemberKey0  
   , Measures.MemberKey1     
   }  ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzando le proprietà del membro &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
