---
title: Errore di gestione (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f612a88976890a95b8fbd3d28826685d0e4ef414
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="error-handling-mdx"></a>Gestione degli errori (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Ogni cubo può controllare la modalità con cui verranno gestiti gli errori di uno script MDX (Multidimensional Expressions). La gestione degli errori viene eseguita tramite l'enumeratore **ScriptErrorHandlingMode** . I possibili valori dell'enumeratore sono i seguenti:  
  
 **IgnoreNone**  
 Induce il server a generare un errore quando [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] rileva un errore nello script MDX.  
  
 **IgnoreAll**  
 Induce il server a ignorare tutti i comandi dello script MDX che contengono un errore, compresi gli errori di sintassi e gli errori di risoluzione dei nomi.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
