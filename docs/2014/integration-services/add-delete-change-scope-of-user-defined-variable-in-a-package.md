---
title: Aggiungere, eliminare o modificare l'ambito della variabile definita dall'utente in un pacchetto | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- variables [Integration Services], adding
ms.assetid: cbf40c7f-3c8a-48cd-aefa-8b37faf8b40e
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: abc9f00432128750e4b61e971038bbc32dd85e86
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125701"
---
# <a name="add-delete-change-scope-of-user-defined-variable-in-a-package"></a>Aggiungere, eliminare o modificare l'ambito di una variabile definita dall'utente in un pacchetto
  In queste procedure viene descritto come aggiungere, eliminare e modificare l'ambito di una variabile definita dall'utente in un pacchetto tramite la finestra **Variabili**.  
  
 Per altre informazioni sull'ambito delle variabili, vedere [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fornisce anche le variabili di sistema che rendono disponibili le informazioni di sistema in fase di esecuzione e sono utilizzabili in contenitori come pacchetti e gestori di eventi. Le variabili di sistema non possono essere eliminate.  
  
### <a name="to-add-a-variable"></a>Per aggiungere una variabile  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il pacchetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che si desidera utilizzare.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  In Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] eseguire una delle operazioni seguenti per definire l'ambito della variabile:  
  
    -   Per impostare il pacchetto come ambito, fare clic in un punto qualsiasi dell'area di progettazione della scheda **Flusso di controllo** .  
  
    -   Per impostare un gestore dell'evento come ambito, selezionare un file eseguibile e un gestore dell'evento nell'area di progettazione della scheda **Gestore evento** .  
  
    -   Per impostare un'attività o un contenitore come ambito, nell'area di progettazione della scheda **Flusso di controllo** o **Gestore evento** fare clic su un'attività o un contenitore.  
  
4.  Scegliere **Variabili** dal menu **SSIS**. Facoltativamente, è possibile visualizzare la finestra **Variabili** eseguendo il mapping del comando View.Variables a una combinazione di tasti scelta dall'utente nella pagina **Tastiera** della finestra di dialogo **Opzioni** .  
  
5.  Nella finestra **Variabili** fare clic sull'icona **Aggiungi variabile** . La nuova variabile verrà aggiunta all'elenco.  
  
6.  Facoltativamente, fare clic sull'icona **Opzioni griglia** , selezionare le colonne aggiuntive da visualizzare nella finestra di dialogo **Variables Grid Options** (Opzioni griglia variabili) e quindi fare clic su **OK**.  
  
7.  Facoltativamente, impostare le proprietà delle variabili. Per altre informazioni, vedere [Impostazione delle proprietà di una variabile definita dall'utente](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md).  
  
8.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
### <a name="to-delete-a-variable"></a>Per eliminare una variabile  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul pacchetto in modo da aprirlo.  
  
3.  Scegliere **Variabili** dal menu **SSIS**. Facoltativamente, è possibile visualizzare la finestra **Variabili** eseguendo il mapping del comando View.Variables a una combinazione di tasti scelta dall'utente nella pagina **Tastiera** della finestra di dialogo **Opzioni** .  
  
4.  Selezionare la variabile che si desidera eliminare e quindi fare clic su **Elimina variabile**.  
  
     Se la variabile non è visualizzata nella finestra Variabili, fare clic su **Opzioni griglia** , quindi selezionare **Mostra variabili di tutti gli ambiti**.  
  
5.  Se viene visualizzata la finestra di dialogo **Conferma eliminazione variabili** , fare clic su **Sì** per confermare.  
  
6.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
### <a name="to-change-the-scope-of-a-variable"></a>Per modificare l'ambito di una variabile  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul pacchetto in modo da aprirlo.  
  
3.  Scegliere **Variabili** dal menu **SSIS**. Facoltativamente, è possibile visualizzare la finestra **Variabili** eseguendo il mapping del comando View.Variables a una combinazione di tasti scelta dall'utente nella pagina **Tastiera** della finestra di dialogo **Opzioni** .  
  
4.  Selezionare la variabile e quindi fare clic su **Sposta variabile**.  
  
     Se la variabile non è visualizzata nella finestra Variabili, fare clic su **Opzioni griglia** , quindi selezionare **Mostra variabili di tutti gli ambiti**.  
  
5.  Nella finestra di dialogo **Seleziona nuovo ambito** selezionare il pacchetto oppure un contenitore, un'attività o un gestore eventi del pacchetto per modificare l'ambito della variabile.  
  
6.  Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Integration Services &#40;SSIS&#41; le variabili](integration-services-ssis-variables.md)   
 [Utilizzo di variabili nei pacchetti](../../2014/integration-services/use-variables-in-packages.md)   
 [Impostare le proprietà di una variabile definita dall'utente](../../2014/integration-services/set-the-properties-of-a-user-defined-variable.md)   
 [Usare i valori di variabili e parametri in un pacchetto figlio](../../2014/integration-services/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
  
