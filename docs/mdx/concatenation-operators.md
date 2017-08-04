---
title: Concatenazione (operatori) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- concatenation operators [MDX]
ms.assetid: 9e4c181a-b71e-41ec-98a1-ec8b5b5103b1
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ae299577ece2c712504631fb85eeac4499c4d4c7
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="concatenation-operators"></a>Operatori di concatenazione
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  L'operatore di concatenazione è rappresentato dal segno più (+). È possibile combinare, o concatenare, due o più stringhe di caratteri in modo da formare una singola stringa, nonché concatenare stringhe binarie.  
  
 Nell'esempio di codice seguente l'operatore di concatenazione viene utilizzato per combinare il nome di un prodotto con il nome univoco del prodotto:  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>Considerazioni sul linguaggio  
 Se le stringhe utilizzate in un'operazione di concatenazione hanno le stesse regole di confronto, le regole di confronto dell'input verranno utilizzate anche per la stringa risultante dalla concatenazione. Se invece le stringhe utilizzate in un'operazione di concatenazione hanno regole di confronto diverse, le regole di confronto della stringa risultante dalla concatenazione verranno determinate in base alla precedenza delle regole di confronto. Per altre informazioni, vedere [Lingue e regole di confronto &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operatori &#40; La sintassi MDX &#41;](../mdx/operators-mdx-syntax.md)  
  
  

