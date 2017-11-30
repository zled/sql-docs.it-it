---
title: CoalesceEmpty (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COALESCEEMPTY
dev_langs: kbMDX
helpviewer_keywords: CoalesceEmpty function
ms.assetid: c00dd739-44bc-4af6-9871-c7e1e3f3e5ba
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d2077f6e268d37839a20bed93c32efbd3c98412f
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="coalesceempty-mdx"></a>CoalesceEmpty (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Converte un valore di cella vuota in un valore di cella non vuota specificato, che può corrispondere a un numero o una stringa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Numeric syntax  
CoalesceEmpty( Numeric_Expression1 [ ,Numeric_Expression2,...n] )  
  
String syntax  
CoalesceEmpty(String_Expression1 [ ,String_Expression2,...n] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Numeric_Expression1*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
 *Numeric_Expression2*  
 Espressione numerica valida che in genere è un valore numerico specificato.  
  
 *String_Expression1*  
 Espressione stringa valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce una stringa.  
  
 *String_Expression2*  
 Espressione stringa valida che in genere è un valore stringa specificato con cui viene sostituito un valore NULL restituito dalla prima espressione stringa.  
  
## <a name="remarks"></a>Osservazioni  
 Se vengono specificate uno o più espressioni numeriche, di **CoalesceEmpty** funzione restituisce il valore numerico della prima espressione numerica, da sinistra a destra, che può essere risolta in un valore non vuoto. Se nessuna delle espressioni numeriche specificate può essere risolta in un valore non vuoto, la funzione restituisce il valore di cella vuota. Il valore della seconda espressione numerica è in genere il valore numerico con cui viene sostituito un valore NULL restituito dalla prima espressione numerica.  
  
 Se vengono specificate una o più espressioni stringa, la funzione restituisce il valore stringa della prima espressione stringa, da sinistra a destra, che può essere risolta in un valore non vuoto. Se nessuna delle espressioni stringa specificate può essere risolta in un valore non vuoto, la funzione restituisce il valore di cella vuota. Il valore della seconda espressione stringa è in genere il valore stringa con cui viene sostituito un valore NULL restituito dalla prima espressione stringa.  
  
 Il **CoalesceEmpty** funzione può accettare solo valori dello stesso tipo. In altre parole, tutte le espressioni valore specificate devono restituire solo tipi di dati numerici o un valore di cella vuota oppure tutte le espressioni valore specificate devono restituire tipi di dati stringa o un valore di cella vuota. Nella stessa chiamata a questa funzione non possono essere incluse espressioni numeriche e stringa.  
  
 Per ulteriori informazioni sulle celle vuote, vedere la documentazione relativa a OLE DB.  
  
## <a name="example"></a>Esempio  
 Le query di esempio seguente il **Adventure Works** cubo. Nell'esempio viene restituito il quantitativo ordinato di ogni prodotto e la percentuale di quantitativi ordinati per categoria. Il **CoalesceEmpty** funzione assicura che i valori null vengono rappresentati come zero (0) durante la formattazione dei membri calcolati.  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
