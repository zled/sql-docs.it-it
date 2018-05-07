---
title: MeasureGroupMeasures (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- MeasureGroupMeasures function
ms.assetid: 69d9b205-1ca7-4741-9ca9-c7926bc87ead
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: bad3fd8693c2d12cdf4a79801cc7d56ec050971a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="measuregroupmeasures-mdx"></a>MeasureGroupMeasures (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
