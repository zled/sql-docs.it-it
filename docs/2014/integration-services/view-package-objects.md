---
title: Visualizzare oggetti di pacchetto | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 568773a255c6a1d264544ef540d88fa6afa0d277
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163251"
---
# <a name="view-package-objects"></a>Visualizzazione di oggetti di pacchetto
  In Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] è disponibile la scheda **Esplora pacchetti** , che consente di visualizzare i pacchetti in una modalità simile a quella di Esplora risorse. La visualizzazione riflette la gerarchia dei contenitori dell'architettura di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Il contenitore del pacchetto si trova al livello principale della gerarchia. Espandendo il pacchetto è possibile visualizzare le connessioni, gli eseguibili, i gestori di eventi, i provider di log, i vincoli di precedenza e le variabili del pacchetto.  
  
 Gli eseguibili, ovvero i contenitori e le attività nel pacchetto, possono includere gestori di eventi, vincoli di precedenza e variabili. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] supporta una gerarchia nidificata di contenitori. A loro volta, i contenitori Ciclo For, Ciclo Foreach e Sequenza possono includere altri eseguibili.  
  
 Se un pacchetto include un flusso di dati, in **Esplora pacchetti** verranno visualizzate l'attività Flusso di dati e una cartella **Componenti** contenente l'elenco dei componenti del flusso di dati.  
  
 Dalla scheda **Esplora pacchetti** è possibile eliminare oggetti da un pacchetto e accedere alla finestra **Proprietà** per visualizzare le proprietà degli oggetti.  
  
 Nella figura seguente viene illustrata l'albero di un semplice pacchetto.  
  
 ![Schermata della scheda Esplora pacchetti](media/packageexplorer.gif "Schermata della scheda Esplora pacchetti")  
  
### <a name="to-view-package-content"></a>Per visualizzare il contenuto di un pacchetto  
  
-   [Visualizzazione degli oggetti dei pacchetti in Esplora pacchetti](../../2014/integration-services/view-package-objects-in-package-explorer.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di Integration Services](control-flow/integration-services-tasks.md)   
 [Contenitori in Integration Services](control-flow/integration-services-containers.md)   
 [Vincoli di precedenza](control-flow/precedence-constraints.md)   
 [Integration Services &#40;SSIS&#41; le variabili](integration-services-ssis-variables.md)   
 [Gestori eventi di Integration Services &#40;SSIS&#41;](integration-services-ssis-event-handlers.md)   
 [Registrazione di Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
