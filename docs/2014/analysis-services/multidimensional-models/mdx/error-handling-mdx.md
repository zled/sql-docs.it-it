---
title: (MDX MultiDimensional Expression) di gestione degli errori | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bbbe021cbb65803f79a4aa0a92791441e22e9cb6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332681"
---
# <a name="error-handling-mdx"></a>Gestione degli errori (MDX)
  Ogni cubo può controllare la modalità con cui verranno gestiti gli errori di uno script MDX (Multidimensional Expressions). Gestione degli errori viene eseguita tramite il `ScriptErrorHandlingMode` enumeratore. I possibili valori dell'enumeratore sono i seguenti:  
  
 `IgnoreNone`  
 Induce il server a generare un errore quando [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rileva un errore nello script MDX.  
  
 `IgnoreAll`  
 Induce il server a ignorare tutti i comandi dello script MDX che contengono un errore, compresi gli errori di sintassi e gli errori di risoluzione dei nomi.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
