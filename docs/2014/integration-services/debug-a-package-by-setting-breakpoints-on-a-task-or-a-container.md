---
title: Debug di un pacchetto impostando punti di interruzione in un'attività o un contenitore | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- containers [Integration Services], breakpoints
- breakpoints [Integration Services]
- tasks [Integration Services], breakpoints
ms.assetid: e7fa106a-2221-403a-bb74-efc9f12bb450
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6535657a5b193b92b76fd32fee9497e8ef76580e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169944"
---
# <a name="debug-a-package-by-setting-breakpoints-on-a-task-or-a-container"></a>Debug di un pacchetto impostando punti di interruzione in un'attività o in un contenitore
  In questa procedura viene descritto come impostare punti di interruzione in un pacchetto, in un'attività o in un contenitore Ciclo For, Ciclo Foreach o Sequenza.  
  
### <a name="to-set-breakpoints-in-a-package-a-task-or-a-container"></a>Per impostare punti di interruzione in un pacchetto, in un'attività o in un contenitore  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  Fare doppio clic sul pacchetto in cui si desidera impostare punti di interruzione.  
  
3.  In Progettazione SSIS eseguire una delle operazioni seguenti:  
  
    -   Per impostare punti di interruzione nell'oggetto di pacchetto, nella scheda **Flusso di controllo** posizionare il cursore in un punto qualsiasi dello sfondo dell'area di progettazione, fare clic con il pulsante destro del mouse e quindi scegliere **Modifica punti di interruzione**.  
  
    -   Per impostare punti di interruzione nel flusso di controllo di un pacchetto, nella scheda **Flusso di controllo** fare clic con il pulsante destro del mouse su un'attività o su un contenitore Ciclo For, Ciclo Foreach o Sequenza e quindi scegliere **Modifica punti di interruzione**.  
  
    -   Per impostare punti di interruzione in un gestore evento, nella scheda **Gestore evento** fare clic con il pulsante destro del mouse su un'attività o su un contenitore Ciclo For, Ciclo Foreach o Sequenza e quindi scegliere **Modifica punti di interruzione**.  
  
4.  Nella finestra di dialogo **Imposta punti di interruzione \<nome contenitore>** selezionare i punti di interruzione da attivare.  
  
5.  Facoltativamente, modificare il tipo di passaggi e il numero di passaggi per ogni punto di interruzione.  
  
6.  Per salvare il pacchetto, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti di risoluzione dei problemi per lo sviluppo di pacchetti](troubleshooting/troubleshooting-tools-for-package-development.md)   
 [Eseguire il debug di uno Script impostando punti di interruzione in un'attività Script e componente Script](data-flow/transformations/script-component.md)   
 [La codifica e debug dell'attività Script](control-flow/script-task.md)   
 [Codifica e debug del componente script](extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
  
  