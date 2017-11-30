---
title: Istruzione REFRESH CUBE (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Cube
- REFRESH CUBE
- REFRESH_CUBE
- REFRESH
dev_langs: kbMDX
helpviewer_keywords:
- cubes [Analysis Services], cache
- refreshing cache
- REFRESH CUBE statement
- cache [Analysis Services]
ms.assetid: b8c087fb-5d17-4b13-b7cf-9929e9aab35c
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 387b16e4d3570655b75bd548d6c2b5cd9e631d1b
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="mdx-data-definition---refresh-cube"></a>Definizione dei dati MDX - aggiornamento cubo
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Aggiorna la cache del client per un cubo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>Argomenti  
 *Cube_Name*  
 Espressione stringa valida che specifica il nome di un cubo.  
  
## <a name="remarks"></a>Osservazioni  
 Per le applicazioni client connesse a un'istanza di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], fa in modo che la memoria nella cache dell'applicazione client deve essere sincronizzato con il server. Nonostante il rilevamento e l'aggiornamento vengano in genere eseguiti in modo automatico, l'intervallo di tempo prima che ciò si verifichi dipende dalle impostazioni della stringa di connessione client. L'istruzione REFRESH CUBE determina l'aggiornamento immediato dei dati.  
  
 Per le applicazioni client connesse a un cubo locale, con l'istruzione REFRESH CUBE il file del cubo locale viene ricompilato.  
  
> [!IMPORTANT]  
>  I set denominati archiviati nel server non vengono aggiornati.  
  
## <a name="see-also"></a>Vedere anche  
 [Le istruzioni di definizione dei dati MDX &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
