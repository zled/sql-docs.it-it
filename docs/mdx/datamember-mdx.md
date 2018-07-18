---
title: DataMember (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2979799686ad1d97018471111c57670383f7f4f8
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577853"
---
# <a name="datamember-mdx"></a>DataMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il membro dei dati generato dal sistema associato a un membro non foglia di una dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Questa funzione agisce sui membri non foglia in una gerarchia qualsiasi e può essere utilizzata dal [UPDATE CUBE Statement (MDX)](../mdx/mdx-data-manipulation-update-cube.md) per i dati writeback per un membro non foglia direttamente, anziché per i discendenti del membro foglia.  
  
> [!NOTE]  
>  Restituisce il membro specificato se tale membro è un membro foglia o se al membro non foglia non è associato alcun membro dei dati.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa il **DataMember** funzione in una misura calcolata per mostrare la quota di vendite per ogni singolo dipendente:  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Concetti chiave per MDX &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
