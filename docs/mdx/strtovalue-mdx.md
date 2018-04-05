---
title: StrToValue (MDX) | Documenti Microsoft
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
- STRTOVALUE
dev_langs:
- kbMDX
helpviewer_keywords:
- StrToValue function
ms.assetid: 118a9c4f-74a3-48d5-a4f4-318664bc51bc
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 37424120aee0b38303b086019e2fb74a823cdc1b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="strtovalue-mdx"></a>StrToValue (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il valore numerico specificato da una stringa con formato MDX (Multidimensional Expression).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
StrToValue(MDX_Expression [,CONSTRAINED] )   
```  
  
## <a name="arguments"></a>Argomenti  
 *MDX_Expression*  
 Espressione stringa valida che viene risolta, direttamente o indirettamente, in una singola cella.  
  
## <a name="remarks"></a>Osservazioni  
 Il **StrToValue** funzione restituisce il valore numerico specificato dall'espressione MDX. Il **StrToValue** funzione viene in genere utilizzata con funzioni definite dall'utente per la restituzione di un'espressione MDX da una funzione esterna a un'istruzione MDX che può essere risolta in una singola cella.  
  
-   Quando viene utilizzato il flag CONSTRAINED, l'espressione MDX deve contenere solo un valore scalare. Questo flag viene utilizzato per ridurre il rischio di attacchi intrusivi tramite la stringa specificata. Se si specifica un'espressione MDX non direttamente risolvibile in un valore scalare, viene visualizzato l'errore seguente: "Le restrizioni imposte dal flag CONSTRAINED nella funzione STRTOVALUE sono state violate".  
  
-   Quando non viene utilizzato il flag CONSTRAINED, non esistono limiti alla complessità dell'espressione MDX specificata, purché si risolva in un'espressione MDX (Multidimensional Expression) valida che restituisce una singola cella.  
  
> [!NOTE]  
>  La restituzione del risultato di un'espressione MDX come valore numerico è particolarmente utile se tale valore viene archiviato come testo e se si desidera utilizzare i valori restituiti per l'esecuzione di operazioni aritmetiche.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa il **StrToValue** funzione per restituire il peso di ogni bicicletta come valore.  
  
```  
WITH MEMBER Measures.x AS   
StrToValue   
   ([Product].[Product].CurrentMember.Properties ('Weight')  
   ,CONSTRAINED  
   )  
SELECT Measures.x ON 0  
,[Product].[Product].[Product].Members ON 1  
FROM [Adventure Works]  
WHERE [Product].[Product Categories].[Bikes]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
