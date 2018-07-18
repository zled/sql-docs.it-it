---
title: Gli elementi figlio (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d61eb168b01e9b6d48c4c003ba28d0f977026906
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740100"
---
# <a name="children-mdx"></a>Children (MDX)


  Restituisce il set di membri figlio di un membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Il **figli** funzione restituisce un set ordinato che contiene gli elementi figlio di un membro specificato. Se non esistono membri figlio del membro specificato, la funzione restituisce un set vuoto.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituiti i figli del membro United States della gerarchia Geography nella dimensione Geography.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 L'esempio seguente restituisce tutti i membri il **misure** dimensione sull'asse delle colonne, inclusi tutti i membri calcolati e il set di tutti gli elementi figlio del `[Product].[Model Name]` gerarchia sull'asse delle righe dell'attributo di **Adventure Works** cubo.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Versione|Cronologia|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Contenuto modificato:**<br /> - E aggiornati, sintassi degli argomenti per maggiore chiarezza.<br /><br /> : Aggiunta di esempi aggiornati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
