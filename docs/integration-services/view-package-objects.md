---
title: Visualizzare gli oggetti di pacchetto | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4314664538d2f3f328e0fbc48965e2541089a95c
ms.contentlocale: it-it
ms.lasthandoff: 09/26/2017

---
# <a name="view-package-objects"></a>Visualizzazione di oggetti di pacchetto
  In Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] è disponibile la scheda **Esplora pacchetti** , che consente di visualizzare i pacchetti in una modalità simile a quella di Esplora risorse. La visualizzazione riflette la gerarchia dei contenitori dell'architettura di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Il contenitore del pacchetto si trova al livello principale della gerarchia. Espandendo il pacchetto è possibile visualizzare le connessioni, gli eseguibili, i gestori di eventi, i provider di log, i vincoli di precedenza e le variabili del pacchetto.  
  
 Gli eseguibili, ovvero i contenitori e le attività nel pacchetto, possono includere gestori di eventi, vincoli di precedenza e variabili. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] supporta una gerarchia nidificata di contenitori. A loro volta, i contenitori Ciclo For, Ciclo Foreach e Sequenza possono includere altri eseguibili.  
  
 Se un pacchetto include un flusso di dati, in **Esplora pacchetti** verranno visualizzate l'attività Flusso di dati e una cartella **Componenti** contenente l'elenco dei componenti del flusso di dati.  
  
 Dalla scheda **Esplora pacchetti** è possibile eliminare oggetti da un pacchetto e accedere alla finestra **Proprietà** per visualizzare le proprietà degli oggetti.  
  
 Nella figura seguente viene illustrata l'albero di un semplice pacchetto.  
  
 ![Schermata della scheda Esplora pacchetti](../integration-services/media/packageexplorer.gif "schermata della scheda Esplora pacchetti")  
  
## <a name="view-the-package-structure-and-content"></a>Visualizzare la struttura del pacchetto e il contenuto  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto che si desidera visualizzare in **Esplora pacchetti**.  
  
2.  Fare clic sulla scheda **Esplora pacchetti** .  
  
3.  Per visualizzare il contenuto delle cartelle **Variabili**, **Vincoli di precedenza**, **Gestori eventi**, **Gestioni connessioni**, **Provider di log**e **File eseguibili** , espandere ogni cartella.  
  
4.  A seconda della struttura del pacchetto, espandere tutte le cartelle di livello inferiore.  
  
## <a name="view-the-properties-of-a-package-object"></a>Visualizzare le proprietà di un oggetto di pacchetto
  
-   Fare clic su un oggetto con il pulsante destro del mouse, quindi scegliere **Proprietà** per aprire la finestra **Proprietà** .  
  
## <a name="delete-an-object-in-a-package"></a>Eliminare un oggetto in un pacchetto  
  
-   Fare clic con il pulsante destro del mouse su un oggetto, quindi scegliere **Elimina**. 
 
## <a name="see-also"></a>Vedere anche  
 [Attività di Integration Services](../integration-services/control-flow/integration-services-tasks.md)   
 [Contenitori in Integration Services](../integration-services/control-flow/integration-services-containers.md)   
 [Vincoli di precedenza](../integration-services/control-flow/precedence-constraints.md)   
 [Variabili di Integration Services &#40;SSIS&#41;](../integration-services/integration-services-ssis-variables.md)   
 [Integration Services &#40; SSIS &#41; Gestori eventi](../integration-services/integration-services-ssis-event-handlers.md)   
 [Integration Services &#40; SSIS &#41; Registrazione](../integration-services/performance/integration-services-ssis-logging.md)  
  
  
