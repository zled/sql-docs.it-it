---
title: Connessione di componenti in un flusso di dati | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 73a379b190f05f4eedc361b4557afefd700a9664
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="connect-components-in-a-data-flow"></a>Connessione di componenti in un flusso di dati
  Questa procedura descrive la connessione dell'output dei componenti di un flusso di dati ad altri componenti dello stesso flusso di dati.  
Per costruire il flusso di dati in un pacchetto, è possibile usare l'area di progettazione della scheda **Flusso di dati** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Se un flusso di dati contiene due componenti, sarà possibile connetterli connettendo l'output di un'origine o trasformazione all'input di una trasformazione o destinazione. Il connettore tra due componenti del flusso di dati è detto percorso.  
  
 Nella figura seguente viene illustrato un semplice flusso di dati con un componente di origine, due trasformazioni, un componente di destinazione e i percorsi che li connettono.  
  
 ![Data flow](../../integration-services/data-flow/media/mw-dts-08.gif "Data flow")  
  
 Dopo aver connesso i due componenti è possibile visualizzare i metadati dei dati che si spostano lungo il percorso e le proprietà del percorso nella finestra **Editor percorso flusso di dati**. Per altre informazioni, vedere [Percorsi in Integration Services](../../integration-services/data-flow/integration-services-paths.md).  
  
 A un percorso è possibile aggiungere anche un visualizzatore dati, che consente di visualizzare i dati che si spostano tra i componenti del flusso di dati durante l'esecuzione del pacchetto.  
  
### <a name="connect-components-in-a-data-flow"></a>Connessione di componenti in un flusso di dati  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di controllo** , quindi fare doppio clic sull'attività Flusso di dati che contiene il flusso di dati in cui si desidera connettere i componenti.  
  
4.  Nell'area di progettazione della scheda **Flusso di dati** selezionare la trasformazione o l'origine da connettere.  
  
5.  Trascinare la freccia verde dell'output di un'origine o trasformazione a una destinazione o trasformazione. In alcuni componenti flussi di dati sono inclusi output degli errori che è possibile connettere allo stesso modo.  
  
    > [!NOTE]  
    >  Alcuni componenti flussi di dati possono includere più output ed è possibile connettere ogni output a una trasformazione o destinazione diversa.  
  
6.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere o eliminare un componente in un flusso di dati](../../integration-services/data-flow/add-or-delete-a-component-in-a-data-flow.md)   
 [Debug del flusso di dati](../../integration-services/troubleshooting/debugging-data-flow.md) [il flusso di dati](../../integration-services/data-flow/data-flow.md)  
  
  

