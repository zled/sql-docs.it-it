---
title: Comprendere le differenze tra l'esecuzione locale e remoto | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1921a7760e42f101ebf5d9b898972c2b2ab8173b
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a>Differenze tra l'esecuzione locale e remota
  Gli sviluppatori e gli amministratori di pacchetti dovrebbero essere consapevoli dell'esistenza di restrizioni in merito a dove può essere eseguito un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   **Un pacchetto viene eseguito nello stesso computer del programma che viene avviato**. Anche quando un programma carica un pacchetto archiviato in remoto in un altro server, il pacchetto viene eseguito nel computer locale.  
  
-   **È possibile eseguire un pacchetto all'esterno dell'ambiente di sviluppo solo in un computer in cui è installato Integration Services**. Non è possibile eseguire i pacchetti all'esterno di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in un computer client in cui [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] non è installato e le condizioni di licenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbero non consentire l'installazione di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in computer aggiuntivi. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è un componente server e non è ridistribuibile ai computer client. Per eseguire pacchetti da un computer client, è necessario avviarli in modo da assicurarsi che vengano eseguiti nel server.  
  
 Per ulteriori informazioni sul caricamento e l'esecuzione di un pacchetto salvato, vedere:  
  
-   [Caricamento ed esecuzione di un pacchetto locale a livello di programmazione](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [Caricamento ed esecuzione di un pacchetto remoto a livello di programmazione](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 Per ulteriori informazioni sull'esecuzione di un pacchetto e il caricamento del relativo output in un programma personalizzato, vedere:  
  
-   [Caricamento dell'output di un pacchetto locale](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Caricamento ed esecuzione di un pacchetto locale a livello di codice](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Caricamento ed esecuzione di un pacchetto remoto a livello di codice](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [Caricamento dell'output di un pacchetto locale](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
