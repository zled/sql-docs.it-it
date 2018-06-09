---
title: UserName (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f8c08855d70d6a880607cc4310e6adcabbf7d9ad
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743480"
---
# <a name="username-mdx"></a>UserName (MDX)


  Restituisce il nome utente e di dominio della connessione corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>Remarks  
 Il valore restituito è costituito da una stringa con il formato seguente:  
  
 *nome dominio\nome utente di dominio*  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il nome dell'utente che esegue la query.  
  
```  
WITH MEMBER Measures.x AS UserName  
SELECT Measures.x ON COLUMNS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
