---
title: MeasureGroupMeasures (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: MeasureGroupMeasures function
ms.assetid: 69d9b205-1ca7-4741-9ca9-c7926bc87ead
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: baacb5ee83ecd45bc994cc462b04d35d6d3ca15a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un set di misure appartenente al gruppo di misure specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
MEASUREGROUPMEASURES(MeasureGroupName)  
```  
  
## <a name="arguments"></a>Argomenti  
 *MeasureGroupName*  
 Espressione stringa valida contenente il nome del gruppo di misure da cui recuperare il set di misure.  
  
## <a name="remarks"></a>Osservazioni  
 La stringa specificata deve corrispondere esattamente al nome del gruppo di misure. Non è necessario racchiudere tra parentesi quadre i nomi di gruppi di misure contenenti spazi.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituite tutte le misure nel gruppo di misure Internet Sales nel cubo Adventure Works.  
  
```  
SELECT MeasureGroupMeasures('Internet Sales') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
