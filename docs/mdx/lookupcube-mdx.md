---
title: LookupCube (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- LOOKUPCUBE
dev_langs:
- kbMDX
helpviewer_keywords:
- LookupCube function
ms.assetid: 243fa101-328a-4016-86e0-d8b5977e15a9
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 41aed2def9e470d39f006b314f51dbb61bf63b47
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="lookupcube-mdx"></a>LookupCube (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore di un'espressione MDX (Multidimensional Expression) valutata su un altro cubo specificato nello stesso database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Numeric expression syntax  
LookupCube(Cube_Name, Numeric_Expression )  
  
String expression syntax  
LookupCube(Cube_Name, String_Expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Espressione stringa valida che specifica il nome di un cubo.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
 *String_Expression*  
 Espressione stringa valida che in genere è un'espressione MDX (Multidimensional Expression) valida di coordinate di celle che restituisce una stringa.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificata un'espressione numerica, la **LookupCube** funzione valuta l'espressione numerica specificata nel cubo specificato e restituisce il valore numerico risultante.  
  
 Se viene specificata un'espressione di stringa, il **LookupCube** funzione valuta l'espressione stringa specificata nel cubo specificato e restituisce il valore di stringa risultante.  
  
 Il **LookupCube** funzione funziona su cubi dello stesso database del cubo di origine in cui la query MDX che contiene il **LookupCube** funzione è in esecuzione.  
  
> [!IMPORTANT]  
>  Poiché il contesto della query corrente non viene trasferito al cubo sul quale viene eseguita la query, tutti i membri correnti necessari devono essere specificati nell'espressione numerica o stringa.  
  
 Qualsiasi calcolo eseguito utilizzando il **LookupCube** funzione è soggetto a problemi di prestazioni ridotte. Anziché utilizzare questa funzione, riprogettare la soluzione in modo che tutti i dati necessari siano presenti in un cubo.  
  
## <a name="examples"></a>Esempi  
 Nella query seguente viene illustrato l'utilizzo di LookupCube:  
  
 `WITH MEMBER MEASURES.LOOKUPCUBEDEMO AS`  
  
 `LOOKUPCUBE("Adventure Works", "[Measures].[In" + "ternet Sales Amount]")`  
  
 `SELECT MEASURES.LOOKUPCUBEDEMO  ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

