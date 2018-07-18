---
title: StrToSet (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 30a69fa1c80c453aabea282d4e6293e28e244069
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582183"
---
# <a name="strtoset-mdx"></a>StrToSet (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il set specificato da una stringa con formattazione MDX (Multidimensional Expression).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
StrToSet(Set_Specification [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Specification*  
 Espressione stringa valida che specifica, direttamente o indirettamente, un set.  
  
## <a name="remarks"></a>Remarks  
 Il **StrToSet** funzione restituisce il set specificato nell'espressione stringa. Il **StrToSet** funzione viene in genere utilizzata con funzioni definite dall'utente per restituire una specifica di set da una funzione esterna a un'istruzione MDX o quando una query MDX con parametri.  
  
-   Quando viene utilizzato il flag CONSTRAINED, la specifica di set deve contenere nomi di membri completi o non qualificati o un set di tuple contenente i nomi dei membri completi o non qualificati racchiusi tra parentesi graffe {}. Questo flag viene utilizzato per ridurre il rischio di attacchi intrusivi tramite la stringa specificata. Se si specifica una stringa non direttamente risolvibile in nomi di membro completi o non qualificati, verrà visualizzato l'errore seguente: "Le restrizioni imposte dal flag CONSTRAINED nella funzione STRTOSET sono state violate".  
  
-   Quando non viene utilizzato il flag CONSTRAINED, è possibile risolvere la specifica di set specificata in un'espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
-   Per comprendere meglio le differenze tra set e membri, vedere Utilizzo di espressioni set e Utilizzo delle espressioni di membro.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce il set di membri della gerarchia dell'attributo State-Province tramite la **StrToSet** (funzione). La specifica di set contiene un'espressione set MDX valida.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members')  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito un errore a causa del flag CONSTRAINED. Sebbene la specifica di set contenga un'espressione MDX valida, per il flag CONSTRAINED la specifica di set deve includere nomi di membri completi o non qualificati.  
  
```  
SELECT StrToSet ('[Geography].[State-Province].Members', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituita la misura Reseller Sales Amount per Germania e Canada. La specifica di set inclusa nella stringa specificata contiene nomi di membri completi, come richiesto dal flag CONSTRAINED.  
  
```  
SELECT StrToSet ('{[Geography].[Geography].[Country].[Germany],[Geography].[Geography].[Country].[Canada]}', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
