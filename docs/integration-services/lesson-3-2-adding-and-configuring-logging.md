---
title: 'Passaggio 2: Aggiunta e configurazione di funzionalità di registrazione | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: 56105f3f-e500-4669-8c8e-acf434527727
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3d28fe017e3757b3f21d6d735911692708eb66c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47726659"
---
# <a name="lesson-3-2---adding-and-configuring-logging"></a>Lezione 3-2: Aggiunta e configurazione di funzionalità di registrazione
In questa attività verrà abilitata la registrazione per il flusso di dati del pacchetto Lesson 3.dtsx. Successivamente un provider di log per file di testo verrà configurato in modo da registrare gli eventi PipelineExecutionPlan e PipelineExecuteTrees. Il provider di log per file di testo crea log facili da visualizzare e da spostare. La semplicità di questi file di log li rende particolarmente utili nella fase di test di base di un pacchetto. Le voci di log possono essere visualizzate anche nella finestra Registra eventi di Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
### <a name="to-add-logging-to-the-package"></a>Per aggiungere le funzionalità di registrazione al pacchetto  
  
1.  Scegliere **Registrazione** dal menu **SSIS**.  
  
2.  Nel riquadro **Contenitori** della finestra di dialogo **Configura log SSIS** verificare che sia selezionato l'oggetto in prima posizione, che rappresenta il pacchetto della lezione 3.  
  
3.  Nella casella **Tipo provider** della scheda **Provider e log** selezionare **Provider di log SSIS per file di testo**e quindi fare clic su **Aggiungi**.  
  
    Integration Services consente di aggiungere un nuovo provider di log per file di testo al pacchetto con il nome predefinito **Provider di log SSIS per file di testo**. È ora possibile configurare il nuovo provider di log.  
  
4.  Nella colonna **Nome** digitare **Lesson 3 Log File**.  
  
5.  Facoltativamente, modificare la **Descrizione**.  
  
6.  Nella colonna **Configurazione** fare clic su **<New Connection>** per specificare la destinazione nella quale verranno scritte le informazioni sulla registrazione.  
  
    Nella finestra di dialogo **Editor gestione connessione file** per **Tipo di utilizzo**selezionare **Crea file**e quindi fare clic su **Sfoglia**. Per impostazione predefinita, la finestra di dialogo **Seleziona file** apre la cartella di progetto; tuttavia è possibile salvare le informazioni sulla registrazione in qualsiasi posizione.  
  
7.  Nella casella **Nome file** della finestra di dialogo **Seleziona file** digitare **TutorialLog.log**e quindi fare clic su **Apri**.  
  
8.  Fare clic su **OK** per chiudere la finestra di dialogo **Editor gestione connessione file** .  
  
9. Nel riquadro **Contenitori** espandere tutti i nodi della gerarchia del contenitore del pacchetto e quindi deselezionare tutte le caselle di controllo, compresa **Extract Sample Currency Data** . Selezionare quindi la casella di controllo **Extract Sample Currency Data** per ottenere solo gli eventi relativi a tale nodo.  
  
    > [!IMPORTANT]  
    > Se la casella di controllo **Extract Sample Currency Data** risulta non disponibile anziché selezionata, l'attività usa le impostazioni log del contenitore padre e non è possibile attivare gli eventi specifici dell'attività.  
  
10. Nella colonna **Eventi** della scheda **Dettagli** selezionare gli eventi **PipelineExecutionPlan** e **PipelineExecutionTrees** .  
  
11. Fare clic su **Avanzate** per controllare i dettagli che verranno scritti nel log per ogni evento. Per impostazione predefinita, tutte le categorie delle informazioni vengono automaticamente selezionate per gli eventi specificati.  
  
12. Fare clic su **Standard** per nascondere le categorie delle informazioni.  
  
13. Nella colonna **Nome** della scheda **Provider e log** selezionare **Lesson 3 Log File**. Dopo aver creato un provider di log per il pacchetto, è possibile disabilitare temporaneamente la registrazione senza la necessità di eliminarlo e ricrearlo.  
  
14. Fare clic su **OK**.  
  
## <a name="next-steps"></a>Next Steps  
[Passaggio 3: Test del pacchetto creato nella lezione 3 dell'esercitazione](../integration-services/lesson-3-3-testing-the-lesson-3-tutorial-package.md)  
  
