---
title: Istruzione CLEAR CALCULATIONS (MDX) | Documenti Microsoft
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
- CLEAR CALCULATIONS
- clalculations
- clear
dev_langs:
- kbMDX
helpviewer_keywords:
- clearing calculations
- CLEAR CALCULATIONS statement
- deleting calculations
- removing calculations
- calculations [Analysis Services], clearing
- cubes [Analysis Services], calculations
ms.assetid: aebec9a1-1d1d-4697-aa3f-cc2449625603
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 042c7b9bedc396d63aa70d23926728b015527a99
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-manipulation---clear-calculations"></a>Manipolazione dei dati MDX - CLEAR CALCULATIONS
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove tutti i calcoli dal cubo e ripristina la sessione di calcolo 0 del cubo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Expression*  
 Espressione di cubo MDX (Multidimensional Expression) valida.  
  
## <a name="remarks"></a>Osservazioni  
 Il **FROM** clausola può essere omessa quando il contesto del cubo è noto, ad esempio uno script MDX.  
  
> [!NOTE]  
>  Questa istruzione può essere eseguita soltanto da un amministratore di database o del server oppure da un membro di un ruolo che ha accesso ai dati di origine nel cubo (ReadSourceData=true)  
  
## <a name="see-also"></a>Vedere anche  
 [Le istruzioni di manipolazione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  

