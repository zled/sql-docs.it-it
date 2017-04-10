---
title: "Debug di un pacchetto impostando punti di interruzione in un&#39;attivit&#224; o in un contenitore | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contenitori [Integration Services], punti di interruzione"
  - "punti di interruzione [Integration Services]"
  - "attività [Integration Services], punti di interruzione"
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# Debug di un pacchetto impostando punti di interruzione in un&#39;attivit&#224; o in un contenitore
  In questa procedura viene descritto come impostare punti di interruzione in un pacchetto, in un'attività o in un contenitore Ciclo For, Ciclo Foreach o Sequenza.  
  
### Per impostare punti di interruzione in un pacchetto, in un'attività o in un contenitore  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  Fare doppio clic sul pacchetto in cui si desidera impostare punti di interruzione.  
  
3.  In Progettazione SSIS eseguire una delle operazioni seguenti:  
  
    -   Per impostare punti di interruzione nell'oggetto di pacchetto, nella scheda **Flusso di controllo** posizionare il cursore in un punto qualsiasi dello sfondo dell'area di progettazione, fare clic con il pulsante destro del mouse e quindi scegliere **Modifica punti di interruzione**.  
  
    -   Per impostare punti di interruzione nel flusso di controllo di un pacchetto, nella scheda **Flusso di controllo** fare clic con il pulsante destro del mouse su un'attività o su un contenitore Ciclo For, Ciclo Foreach o Sequenza e quindi scegliere **Modifica punti di interruzione**.  
  
    -   Per impostare punti di interruzione in un gestore evento, nella scheda **Gestore evento** fare clic con il pulsante destro del mouse su un'attività o su un contenitore Ciclo For, Ciclo Foreach o Sequenza e quindi scegliere **Modifica punti di interruzione**.  
  
4.  Nella finestra di dialogo **Imposta punti di interruzione \<nome contenitore>** selezionare il punto di interruzione da attivare.  
  
5.  Facoltativamente, modificare il tipo di passaggi e il numero di passaggi per ogni punto di interruzione.  
  
6.  Per salvare il pacchetto, scegliere **Salva elementi selezionati** dal menu **File**.  
  
## Vedere anche  
 [Risoluzione dei problemi relativi agli strumenti per lo sviluppo dei pacchetti](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)   
 [Eseguire il debug di uno script impostando punti di interruzione in un'attività e in un componente Script](../../integration-services/extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)   
 [Scrittura di codice e debug dell'attività Script](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)   
 [Codifica e debug del componente script](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  