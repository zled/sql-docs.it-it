---
title: CustomData (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 172915d99b231490cbdca24f70d1d38da27a1d3d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739303"
---
# <a name="customdata-mdx"></a>CustomData (MDX)


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
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
