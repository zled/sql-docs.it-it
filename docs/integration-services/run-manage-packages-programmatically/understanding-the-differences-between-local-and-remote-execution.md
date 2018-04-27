---
title: Differenze tra l'esecuzione locale e remota | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: run-manage-packages-programmatically
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3caec713cc1839726a3edf0b8ef81a220e1bc2f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a>Differenze tra l'esecuzione locale e remota
  Gli sviluppatori e gli amministratori di pacchetti dovrebbero essere consapevoli dell'esistenza di restrizioni in merito a dove può essere eseguito un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   **Un pacchetto viene eseguito nello stesso computer del programma che lo avvia**. Anche quando un programma carica un pacchetto archiviato in remoto in un altro server, il pacchetto viene eseguito nel computer locale.  
  
-   **È possibile eseguire un pacchetto all'esterno dell'ambiente di sviluppo solo in un computer in cui è installato Integration Services**. Non è possibile eseguire i pacchetti all'esterno di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in un computer client in cui [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] non è installato e le condizioni di licenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbero non consentire l'installazione di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in computer aggiuntivi. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è un componente server e non è ridistribuibile a computer client. Per eseguire pacchetti da un computer client, è necessario avviarli in modo da assicurarsi che vengano eseguiti nel server.  
  
 Per ulteriori informazioni sul caricamento e l'esecuzione di un pacchetto salvato, vedere:  
  
-   [Caricamento ed esecuzione di un pacchetto locale a livello di programmazione](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [Caricamento ed esecuzione di un pacchetto remoto a livello di programmazione](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 Per ulteriori informazioni sull'esecuzione di un pacchetto e il caricamento del relativo output in un programma personalizzato, vedere:  
  
-   [Caricamento dell'output di un pacchetto locale](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Caricamento ed esecuzione di un pacchetto locale a livello di programmazione](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Caricamento ed esecuzione di un pacchetto remoto a livello di programmazione](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [Caricamento dell'output di un pacchetto locale](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
