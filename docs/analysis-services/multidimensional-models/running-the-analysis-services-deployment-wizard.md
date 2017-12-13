---
title: Eseguire l'analisi dei servizi di distribuzione guidata | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 9a647f65ebbd482fa7f279732685f132d57fcc09
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="running-the-analysis-services-deployment-wizard"></a>Esecuzione della Distribuzione guidata Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Quando si utilizza il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata per distribuire un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto, è possibile eseguire la procedura guidata nei modi seguenti:  
  
-   **In modo interattivo** quando esegue in modo interattivo il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata genera uno script di distribuzione basato su file di input, come modificata in modo interattivo dall'input dell'utente. Tramite la procedura guidata eventuali modifiche apportate dall'utente vengono applicate solo allo script di distribuzione. I file di input non vengono modificati. Per altre informazioni sui file di input, vedere [Informazioni sui file di input usati per creare uno script di distribuzione](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md).  
  
-   **Dal prompt dei comandi** quando esegue il prompt dei comandi, il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata genera uno script di distribuzione in base alle opzioni che consentono di eseguire la procedura guidata. Tramite la procedura guidata potrebbe venire richiesto l'input dell'utente e potrebbero venire modificati i file di input in base a tale input, potrebbe venire eseguita una distribuzione automatica invisibile all'utente oppure potrebbe venire creato uno script di distribuzione da utilizzare successivamente.  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a>Esecuzione della Distribuzione guidata Analysis Services in modo interattivo  
 Quando viene eseguita in modo interattivo, la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] legge i valori dei file di input e presenta le relative informazioni agli utenti. È possibile modificare i valori di input, ad esempio destinazione di distribuzione, impostazioni di configurazione, opzioni di distribuzione e password della stringa di connessione, oppure lasciarli inalterati. Se si modificano i valori di input, la procedura guidata utilizza queste modifiche durante la generazione di script di distribuzione. Tramite la procedura guidata non vengono tuttavia apportate modifiche al file di input.  
  
> [!NOTE]  
>  Se si desidera utilizzare la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per modificare i valori di input, eseguire la procedura guidata al prompt dei comandi e impostarla per l'esecuzione in modalità file di risposte.  
  
 Dopo aver esaminato i valori di input e apportare le modifiche desiderate, la procedura guidata genera script di distribuzione. È possibile eseguire questo script di distribuzione immediatamente nel server di destinazione o salvarlo per utilizzarlo successivamente.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a>Per eseguire la Distribuzione guidata Analysis Services in modo interattivo  
  
-   Fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server**, **Analysis Services**e quindi **Distribuzione guidata**.  
  
     -oppure-  
  
-   Nel **progetti** cartella del [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto, fare doppio clic su di \<nome progetto > file con estensione asdatabase.
    > [!NOTE]  
    >  Se non è possibile trovare il file con estensione asdatabase, provare a utilizzare ricerca e specificare asdatabase. In alternativa, potrebbe essere necessario compilare il progetto in SSDT.  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Esecuzione della Distribuzione guidata Analysis Services al prompt dei comandi  
 La Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] può essere inoltre eseguita al prompt dei comandi. In tal caso, è necessario specificare il percorso completo del file con estensione .asdatabase ed eseguire la procedura guidata in una delle modalità indicate di seguito.  
  
 **Modalità file di risposte**  
 In modalità file di risposte è possibile modificare in modo interattivo i file di input originariamente generati al durante la creazione del progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. La procedura guidata consente di salvare i file di input modificati prima di generare lo script di distribuzione. I file di input modificati diventano il nuovo punto di partenza per la successiva esecuzione della procedura guidata.  
  
 Per eseguire la procedura guidata in modalità file di risposte, usare il **/a** passare.  
  
 **Modalità automatica**  
 In modalità non interattiva viene eseguita una distribuzione automatica invisibile all'utente basata sulle informazioni incluse nei file di input.  
  
 Per eseguire la procedura guidata in modalità invisibile all'utente, utilizzare il **/s** passare. Quando si esegue la procedura guidata in modalità non interattiva, i messaggi vengono inviati alla console o a un file di log, se presente.  
  
 **Modalità output**  
 In modalità output, la procedura guidata genera uno script di distribuzione per un'esecuzione successiva in base ai file di input.  
  
 Per eseguire la procedura guidata in modalità output, usare il **/o** passare e specificare un nome di file di output.  
  
 Per altre informazioni sulle opzioni della riga di comando, vedere [Distribuire soluzioni di modelli con l'utilità di distribuzione](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md).  
  
 Nella procedura seguente viene illustrato come eseguire la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] al prompt dei comandi.  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Per eseguire la Distribuzione guidata Analysis Services al prompt dei comandi  
  
1.  Aprire un prompt dei comandi e passare alla cartella C:\Programmi (x86)\Microsoft SQL Server\120\Tools\Binn\ManagementStudio  
  
2.  Digitare **Microsoft.AnalysisServices.Deployment.exe** seguito dalle opzioni corrispondenti alla modalità in cui si desidera eseguire la procedura guidata.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sullo script di distribuzione di Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)   
 [Distribuire soluzioni di modelli tramite la Distribuzione guidata](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
