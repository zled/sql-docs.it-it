---
title: Connessione di componenti con percorsi | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data flow [Integration Services], connections
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 05633e4c-1370-4b05-802b-f36b07dd71c8
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5152147f82d1d413806eeb8f9644e70af9a04828
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065188"
---
# <a name="connect-components-with-paths"></a>Connessione di componenti con i percorsi
  Per costruire il flusso di dati in un pacchetto, è possibile usare l'area di progettazione della scheda **Flusso di dati** di Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)]. Se un flusso di dati contiene due componenti, sarà possibile connetterli connettendo l'output di un'origine o trasformazione all'input di una trasformazione o destinazione. Il connettore tra due componenti del flusso di dati è detto percorso.  
  
 Nella figura seguente viene illustrato un semplice flusso di dati con un componente di origine, due trasformazioni, un componente di destinazione e i percorsi che li connettono.  
  
 ![Flusso di dati](media/mw-dts-08.gif "flusso di dati")  
  
 Dopo aver connesso i due componenti è possibile visualizzare i metadati dei dati che si spostano lungo il percorso e le proprietà del percorso nella finestra **Editor percorso flusso di dati**. Per altre informazioni, vedere [Percorsi in Integration Services](data-flow/integration-services-paths.md).  
  
 A un percorso è possibile aggiungere anche un visualizzatore dati, che consente di visualizzare i dati che si spostano tra i componenti del flusso di dati durante l'esecuzione del pacchetto.  
  
### <a name="to-connect-components-in-a-data-flow"></a>Per connettere componenti in un flusso di dati  
  
-   [Connettere componenti in un flusso di dati](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-set-path-properties"></a>Per impostare le proprietà di un percorso  
  
-   [Impostare le proprietà di un percorso tramite Editor percorso flusso di dati](../../2014/integration-services/set-the-properties-of-a-path-by-using-the-data-flow-path-editor.md)  
  
### <a name="to-view-path-metadata"></a>Per visualizzare i metadati di un percorso  
  
-   [Visualizzare i metadati di percorso nell'Editor percorso flusso di dati](../../2014/integration-services/view-path-metadata-in-the-data-flow-path-editor.md)  
  
### <a name="to-view-path-metadata"></a>Per visualizzare i metadati di un percorso  
  
-   [Aggiungere un visualizzatore dati a un flusso di dati](../../2014/integration-services/add-a-data-viewer-to-a-data-flow.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Attività Flusso di dati](control-flow/data-flow-task.md)   
 [Flusso di dati](data-flow/data-flow.md)   
 [Trasformazione di dati con le trasformazioni](data-flow/transformations/transform-data-with-transformations.md)   
 [Gestione degli errori nei dati](data-flow/error-handling-in-data.md)  
  
  