---
title: StrToMember (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 37c76d6e1e7ffe9bc40d785952b5c456ab1fc6fa
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743050"
---
# <a name="strtomember-mdx"></a>StrToMember (MDX)


  Restituisce il membro specificato da una stringa in formato MDX (Multidimensional Expression).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
StrToMember(Member_Name [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Name*  
 Espressione stringa valida che specifica, in modo diretto o indiretto, un membro.  
  
## <a name="remarks"></a>Remarks  
 Il **StrToMember** funzione restituisce il membro specificato nell'espressione stringa. Il **StrToMember** funzione viene in genere utilizzata con funzioni definite dall'utente per restituire una specifica del membro da una funzione esterna a un'istruzione MDX o quando una query MDX con parametri.  
  
-   Quando viene utilizzato il flag CONSTRAINED, il nome del membro deve essere direttamente risolvibile in un nome di membro completo o non qualificato. Questo flag viene utilizzato per ridurre il rischio di attacchi intrusivi tramite la stringa specificata. Se viene specificata una stringa non direttamente risolvibile in un nome di membro completo o non qualificato, viene visualizzato l'errore seguente: "Le restrizioni imposte dal flag CONSTRAINED nella funzione STRTOMEMBER sono state violate".  
  
-   Quando non viene utilizzato il flag CONSTRAINED, il membro specificato può essere risolto direttamente nel nome di un membro oppure in un'espressione MDX risolvibile in un nome.  
  
-   Per comprendere meglio le differenze tra set e membri, vedere Utilizzo di espressioni set e Utilizzo delle espressioni di membro.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce la misura Reseller Sales Amount relativa al membro Bayern nella gerarchia dell'attributo State-Province tramite la **StrToMember** (funzione). La stringa specificata ha indicato il nome completo del membro.  
  
```  
SELECT {StrToMember ('[Geography].[State-Province].[Bayern]')}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 L'esempio seguente restituisce la misura Reseller Sales Amount relativa al membro Bayern utilizzando il **StrToMember** (funzione). Poiché con la stringa del nome del membro è stato specificato soltanto un nome di membro non qualificato, la query restituisce la prima istanza del membro specificato, che si trova nella gerarchia Customer Geography della dimensione Customer, che non si interseca con Reseller Sales. Le procedure consigliate prevedono la specifica del nome completo in modo da garantire i risultati previsti.  
  
```  
SELECT {StrToMember ('[Bayern]').Parent}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 L'esempio seguente restituisce la misura Reseller Sales Amount relativa al membro Bayern nella gerarchia dell'attributo State-Province tramite la **StrToMember** (funzione). La stringa del nome del membro specificata viene risolta in un nome di membro completo.  
  
```  
SELECT {StrToMember('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)}  
ON 0,  
{[Measures].[Reseller Sales Amount]} ON 1  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito un errore a causa del flag CONSTRAINED. Nonostante la stringa del nome del membro specificata contenga un'espressione di membro MDX valida che viene risolta in un nome di membro completo, il flag CONSTRAINED richiede nomi di membro completi o non qualificati nella stringa del nome del membro.  
  
```  
SELECT StrToMember ('[Geography].[Geography].[Country].[Germany].FirstChild', CONSTRAINED)  
ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
