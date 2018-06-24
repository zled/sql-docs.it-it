---
title: Debug del flusso di controllo | Microsoft Docs
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
- progress reporting [Integration Services]
- breakpoints [Integration Services]
- debugging [Integration Services], control flow
- control flow [Integration Services], debugging
- color-coded progress reporting [Integration Services]
- Set Breakpoints dialog box
ms.assetid: 54a458cc-9f4f-4b48-8cf2-db2e0fa7756c
caps.latest.revision: 54
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 8b8de78b135245c36d11f4dfb96a993fd0bbc4dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065861"
---
# <a name="debugging-control-flow"></a>Debug del flusso di controllo
  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] e [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] includono funzionalità e strumenti che è possibile utilizzare per risolvere il flusso di controllo in un [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] pacchetto.  
  
-   [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] supporta i punti di interruzione in contenitori e attività.  
  
-   Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] genera report di stato in fase di esecuzione.  
  
-   In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] sono disponibili finestre di debug.  
  
## <a name="breakpoints"></a>Punti di interruzione  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Finestra di progettazione fornisce le **Imposta punti di interruzione** della finestra di dialogo in cui è possibile impostare i punti di interruzione attivando condizioni di interruzione e specificando il numero di volte in cui un punto di interruzione può verificarsi prima dell'esecuzione del pacchetto viene sospeso. I punti di interruzione possono essere abilitati a livello di pacchetto oppure a livello di singolo componente. Se le condizioni di interruzione vengono abilitate a livello di attività o di contenitore, nell'area di progettazione della scheda **Flusso di controllo** accanto all'attività o al contenitore verrà visualizzata l'icona del punto di interruzione. Se le condizioni di interruzione vengono abilitate a livello di pacchetto, l'icona del punto di interruzione verrà visualizzata sull'etichetta della scheda **Flusso di controllo** .  
  
 Quando viene rilevato un punto di interruzione, la relativa icona viene modificata in modo da aiutare l'utente a identificarne l'origine. È possibile aggiungere, eliminare e modificare i punti di interruzione durante l'esecuzione del pacchetto.  
  
 In [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] sono disponibili condizioni di interruzione che è possibile abilitare su tutte le attività e i contenitori. Nella finestra di dialogo **Imposta punti di interruzione** è possibile abilitare punti di interruzione per le condizioni seguenti:  
  
|Condizione di interruzione|Description|  
|---------------------|-----------------|  
|Quando l'attività o il contenitore riceve il `OnPreExecute` evento.|Viene chiamata quando l'attività sta per essere eseguita. Questo evento viene generato da un'attività o da un contenitore immediatamente prima della sua esecuzione.|  
|Quando l'attività o il contenitore riceve il `OnPostExecute` evento.|Viene chiamata immediatamente dopo il termine della logica di esecuzione dell'attività. Questo evento viene generato da un'attività o da un contenitore immediatamente dopo la sua esecuzione.|  
|Quando l'attività o il contenitore riceve il `OnError` evento.|Viene chiamata da un'attività o un contenitore quando si verifica un errore.|  
|Quando l'attività o il contenitore riceve il `OnWarning` evento.|Viene chiamata quando l'attività è in uno stato che non giustifica un errore, ma richiede la visualizzazione di un avviso.|  
|Quando l'attività o il contenitore riceve il `OnInformation` evento.|Viene chiamata quando l'attività deve fornire informazioni.|  
|Quando l'attività o il contenitore riceve il `OnTaskFailed` evento.|Viene chiamata dall'host delle attività in caso di errore.|  
|Quando l'attività o il contenitore riceve il `OnProgress` evento.|Viene chiamata per aggiornare le informazioni sullo stato di esecuzione dell'attività.|  
|Quando l'attività o il contenitore riceve il `OnQueryCancel` evento.|Viene chiamata in qualsiasi momento dell'elaborazione dell'attività in cui è possibile annullare l'esecuzione.|  
|Quando l'attività o il contenitore riceve il `OnVariableValueChanged` evento.|Viene chiamata dal runtime di [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] quando il valore di una variabile viene modificato. RaiseChangeEvent della variabile deve essere impostato su `true` per generare questo evento.<br /><br /> **\*\* Avviso \*\*** La variabile associata a questo punto di interruzione deve essere definita nell'ambito del **contenitore** . Se la variabile viene definita nell'ambito del pacchetto, il punto di interruzione non viene raggiunto.|  
|Quando l'attività o il contenitore riceve il `OnCustomEvent` evento.|Chiamato dalle attività per generare eventi personalizzati definiti per le singole attività.|  
  
 Oltre a quelle disponibili per tutte le attività e i contenitori, alcuni contenitori e attività includono speciali condizioni di interruzione per l'impostazione dei punti di interruzione. Per il contenitore Ciclo For è ad esempio possibile abilitare un punto di interruzione che sospende l'esecuzione all'inizio di ogni iterazione del ciclo.  
  
 Per aumentare la flessibilità e l'efficacia di un punto di interruzione, è possibile modificarne il comportamento specificando le opzioni seguenti:  
  
-   Il numero di passaggi, ovvero il massimo numero di volte per cui può verificarsi una condizione di interruzione prima che l'esecuzione venga sospesa.  
  
-   Il tipo di passaggi, ovvero la regola che specifica in quali casi la condizione di interruzione deve attivare il punto di interruzione.  
  
 Ad eccezione del tipo Sempre, il tipo di passaggi è ulteriormente qualificato dall'opzione Passaggi. Se ad esempio il tipo è "Numero di passaggi uguale a" e l'opzione Passaggi è 5, l'esecuzione verrà sospesa alla sesta occorrenza della condizione di interruzione.  
  
 Nella tabella seguente vengono descritti i tipi di passaggi disponibili.  
  
|Tipo di passaggi|Description|  
|--------------------|-----------------|  
|Always|L'esecuzione viene sempre sospesa al rilevamento di un punto di interruzione.|  
|Numero di passaggi uguale a|L'esecuzione viene sospesa quando il punto di interruzione viene rilevato per un numero di volte uguale al numero di passaggi specificato.|  
|Numero di passaggi maggiore o uguale a|L'esecuzione viene sospesa quando il punto di interruzione viene rilevato per un numero di volte maggiore o uguale al numero di passaggi specificato.|  
|Numero di passaggi multiplo di|L'esecuzione viene sospesa quando il punto di interruzione viene rilevato per un numero di volte multiplo del numero di passaggi specificato. Se ad esempio questa opzione è impostata su 5, l'esecuzione verrà sospesa ogni cinque volte.|  
  
#### <a name="to-set-breakpoints"></a>Per impostare punti di interruzione  
  
-   [Debug di un pacchetto impostando punti di interruzione in un'attività o un contenitore](../debug-a-package-by-setting-breakpoints-on-a-task-or-a-container.md)  
  
## <a name="progress-reporting"></a>Report di stato  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Finestra di progettazione include due tipi di report di stato: codifica a colori nell'area di progettazione del **flusso di controllo** scheda e i messaggi di stato sul **lo stato di avanzamento** scheda.  
  
 Durante l'esecuzione di un pacchetto, Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] indica l'avanzamento dell'esecuzione visualizzando ogni attività o contenitore con un colore che ne indica lo stato di esecuzione. Dal colore è possibile capire se l'elemento è in attesa di esecuzione, in fase di esecuzione, ha terminato l'esecuzione o è stato interrotto senza completare l'esecuzione. Quando l'esecuzione del pacchetto viene arrestata, la codifica a colori non viene più utilizzata.  
  
 Nella tabella seguente vengono descritti i colori utilizzati per indicare lo stato dell'esecuzione.  
  
|Colore|Stato esecuzione|  
|-----------|----------------------|  
|Grigio|In attesa di esecuzione.|  
|Giallo|In esecuzione|  
|Green|L'esecuzione è stata completata.|  
|evidenziazione|Il componente è stato eseguito con errori.|  
  
 La scheda **Stato** elenca i contenitori e le attività in ordine di esecuzione, oltre all'ora di inizio e di fine, agli avvisi e ai messaggi di errore. Dopo l'arresto dell'esecuzione di un pacchetto, le informazioni sullo stato rimangono disponibili nella scheda **Risultati esecuzione** .  
  
> [!NOTE]  
>  Per abilitare o disabilitare la visualizzazione di messaggi nella scheda **Stato** , attivare o disattivare l'opzione **Debug report di stato** del menu **SSIS** .  
  
 Il diagramma illustra la scheda **Stato** .  
  
 ![Scheda Stato di Progettazione SSIS](../media/mw-dtsflow04.gif "Scheda Stato di Progettazione SSIS")  
  
## <a name="debug-windows"></a>Finestre di debug  
 In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] sono disponibili numerose finestre che è possibile utilizzare per la gestione dei punti di interruzione e per il debug dei pacchetti contenenti punti di interruzione. Per ulteriori informazioni su una finestra specifica, aprirla e premere F1 per visualizzare l'argomento della Guida corrispondente.  
  
 Per aprire queste finestre in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], scegliere **Finestre** dal menu **Debug**e quindi **Punti di interruzione**, **Output**o **Controllo immediato**.  
  
 Nella tabella seguente vengono descritte le finestre disponibili.  
  
|Finestra|Description|  
|------------|-----------------|  
|Punti di interruzione|Elenca i punti di interruzione presenti in un pacchetto e include opzioni che consentono di abilitarli ed eliminarli.|  
|Output|Visualizza messaggi di stato per le funzionalità di [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].|  
|Controllo immediato|Consente di valutare espressioni ed eseguirne il debug, nonché di visualizzare i valori delle variabili.|  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti per la risoluzione dei problemi relativi allo sviluppo dei pacchetti](troubleshooting-tools-for-package-development.md)  
  
  