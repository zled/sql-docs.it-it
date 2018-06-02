---
title: UserName (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 887af13c84fd06ead5a36564c0dda740a5f6d0b0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581353"
---
# <a name="username-mdx"></a>UserName (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
  
