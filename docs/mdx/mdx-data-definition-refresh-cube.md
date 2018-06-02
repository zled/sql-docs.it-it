---
title: Istruzione REFRESH CUBE (MDX) | Documenti Microsoft
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f27051d9e0fe1d0a6eb3d580548233eb9f073215
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579773"
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
  
## <a name="remarks"></a>Remarks  
 Per le applicazioni client connesse a un'istanza di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], fa in modo che la memoria nella cache dell'applicazione client deve essere sincronizzato con il server. Nonostante il rilevamento e l'aggiornamento vengano in genere eseguiti in modo automatico, l'intervallo di tempo prima che ciò si verifichi dipende dalle impostazioni della stringa di connessione client. L'istruzione REFRESH CUBE determina l'aggiornamento immediato dei dati.  
  
 Per le applicazioni client connesse a un cubo locale, con l'istruzione REFRESH CUBE il file del cubo locale viene ricompilato.  
  
> [!IMPORTANT]  
>  I set denominati archiviati nel server non vengono aggiornati.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni di definizione dei dati MDX &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
