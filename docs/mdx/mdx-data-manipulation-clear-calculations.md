---
title: Istruzione CLEAR CALCULATIONS (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f210f2ad8af7b0d4e71482946a496d326fe63f24
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579783"
---
# <a name="mdx-data-manipulation---clear-calculations"></a>Manipolazione dei dati MDX - CLEAR CALCULATIONS
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Rimuove tutti i calcoli dal cubo e ripristina la sessione di calcolo 0 del cubo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CLEAR CALCULATIONS [FROMCube_Expression]  
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Expression*  
 Espressione di cubo MDX (Multidimensional Expression) valida.  
  
## <a name="remarks"></a>Remarks  
 Il **FROM** clausola può essere omessa quando il contesto del cubo è noto, ad esempio uno script MDX.  
  
> [!NOTE]  
>  Questa istruzione può essere eseguita soltanto da un amministratore di database o del server oppure da un membro di un ruolo che ha accesso ai dati di origine nel cubo (ReadSourceData=true)  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni MDX di manipolazione dei dati &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
