---
title: Operatori unari | Documenti Microsoft
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
- unary operators
ms.assetid: bf1b5518-6040-4484-9ce8-79c0eb4373a9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 1486ab5907a9c3b738bc9ab23e8154e696766f16
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="unary-operators"></a>Operatori unari
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Nel linguaggio MDX (Multidimensional Expressions) gli operatori unari eseguono un'operazione su un singolo operando, ad esempio la restituzione del valore positivo o negativo di un'espressione numerica.  
  
 MDX supporta gli operatori unari elencati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[- (negativo)](../mdx/negative-mdx.md)|Restituisce l'opposto del valore di un'espressione numerica.|  
|[+ (positivo)](../mdx/positive-mdx.md)|Restituisce il valore positivo di un'espressione numerica.|  
  
 Nell'esempio seguente viene illustrato l'utilizzo di un operatore unario per la restituzione dell'opposto del valore di una misura:  
  
```  
WITH   
   MEMBER [Measures].[NegDiscountAmount] AS  
   -[Measures].[Discount Amount]  
SELECT   
   {[Measures].[Discount Amount],[Measures].[NegDiscountAmount]} on COLUMNS,  
   NON EMPTY [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
WHERE [Product].[Category].[Bikes]  
```  
  
 Inoltre, MDX utilizzare speciali operatori unari per determinare l'operazione di aggregazione eseguita dal [RollupChildren](../mdx/rollupchildren-mdx.md) (funzione). Per ulteriori informazioni su questi operatori unari speciali, vedere [aggiungere un'aggregazione personalizzata a una dimensione](../analysis-services/multidimensional-models/bi-wizard-add-a-custom-aggregation-to-a-dimension.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Gli operatori &#40;sintassi MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
