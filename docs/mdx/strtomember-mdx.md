---
title: StrToMember (MDX) | Documenti Microsoft
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
- STRTOMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToMember function
ms.assetid: eb8a3dc0-5ae4-434e-b321-680a81a59e67
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: b26a0a5922f138bc13bbb13099809629ee336b02
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="strtomember-mdx"></a>StrToMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
