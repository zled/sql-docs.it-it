---
title: CustomData (MDX) | Documenti Microsoft
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
- EXISTS
dev_langs:
- kbMDX
helpviewer_keywords:
- Exists function
ms.assetid: 61d9f5a2-6f56-4179-a39b-317c8e0a2cdd
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 47f1f10a7636a2c53dc897d9e6858ac214281e73
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="customdata-mdx"></a>CustomData (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore della **CustomData** proprietà stringa di connessione, se definito; in caso contrario, **null**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Il **CustomData** funzione consente di recuperare il **CustomData** proprietà della stringa di connessione e passare un'impostazione di configurazione per essere utilizzati dalle funzioni MDX (Multidimensional Expressions) e istruzioni, ad esempio [UserName (MDX)](../mdx/username-mdx.md) e [istruzione CALL (MDX)](../mdx/mdx-data-manipulation-call.md). Ad esempio, questa funzione può essere utilizzata in un'espressione di sicurezza dinamica per selezionare i membri del set consentiti/negati per il valore di stringa nel **CustomData** proprietà della stringa di connessione.  
  
## <a name="example"></a>Esempio  
 La query seguente consente di visualizzare il valore restituito dal **CustomData** funzione in una misura calcolata:  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

