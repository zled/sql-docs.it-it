---
title: Domini applicazione e sicurezza dell'integrazione con CLR | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0c97f958126dc7b19478bf0864a23ce4ab4fe07b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36066143"
---
# <a name="application-domains-and-clr-integration-security"></a>Domini applicazione e sicurezza per l'integrazione con CLR
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono caricati gli assembly che appartengono allo stesso proprietario in un dominio applicazione comune. Grazie a un set di assembly in esecuzione nello stesso dominio applicazione, gli assembly possono individuare altri assembly in fase di esecuzione utilizzando le API di reflection di .NET Framework o altri strumenti e possono effettuare una chiamata in tali assembly in modalità di associazione tardiva. Poiché tali chiamate vengono effettuate verso assembly che appartengono allo stesso proprietario, le autorizzazioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per queste chiamate non vengono controllate. Lo schema di posizione degli assembly nei domini applicazione è stato progettato principalmente per realizzare obiettivi di scalabilità, sicurezza e isolamento e potrebbe cambiare nelle versioni future. Di conseguenza è consigliabile non basarsi sui meccanismi di associazione tardiva per individuare gli assembly nello stesso dominio applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza per l'integrazione con CLR](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  