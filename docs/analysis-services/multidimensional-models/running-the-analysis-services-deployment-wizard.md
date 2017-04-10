---
title: "Esecuzione della Distribuzione guidata Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Distribuzione guidata Analysis Services, esecuzione"
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
caps.latest.revision: 41
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 38
---
# Esecuzione della Distribuzione guidata Analysis Services
  Quando si utilizza Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per distribuire un progetto di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è possibile eseguire la procedura guidata nei modi seguenti:  
  
-   **In modo interattivo** Quando viene eseguita in modo interattivo, la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di generare uno script di distribuzione XML basato sui file in input, in base alle modifiche interattive apportate tramite l'input dell'utente. Tramite la procedura guidata eventuali modifiche apportate dall'utente vengono applicate solo allo script di distribuzione. I file di input non vengono modificati. Per altre informazioni sui file di input, vedere [Informazioni sui file di input usati per creare uno script di distribuzione](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md).  
  
-   **Al prompt dei comandi** Quando viene eseguita al prompt dei comandi, la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di generare uno script di distribuzione \(XMLA\) (XML for Analysis), in base alle opzioni usate per eseguire la procedura guidata. Tramite la procedura guidata potrebbe venire richiesto l'input dell'utente e potrebbero venire modificati i file di input in base a tale input, potrebbe venire eseguita una distribuzione automatica invisibile all'utente oppure potrebbe venire creato uno script di distribuzione da utilizzare successivamente.  
  
## Esecuzione della Distribuzione guidata Analysis Services in modo interattivo  
 Quando viene eseguita in modo interattivo, la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] legge i valori dei file di input e presenta le relative informazioni agli utenti. È possibile modificare i valori di input, ad esempio destinazione di distribuzione, impostazioni di configurazione, opzioni di distribuzione e password della stringa di connessione, oppure lasciarli inalterati. Se si modificano i valori di input, le modifiche vengono utilizzate dalla procedura guidata per la creazione dello script di distribuzione XMLA. Tramite la procedura guidata non vengono tuttavia apportate modifiche al file di input.  
  
> [!NOTE]  
>  Se si desidera utilizzare la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per modificare i valori di input, eseguire la procedura guidata al prompt dei comandi e impostarla per l'esecuzione in modalità file di risposte.  
  
 Dopo avere verificato i valori di input e avere apportato le modifiche desiderate, tramite la procedura guidata verrà generato uno script di distribuzione XMLA. È possibile eseguire questo script di distribuzione immediatamente nel server di destinazione o salvarlo per utilizzarlo successivamente.  
  
#### Per eseguire la Distribuzione guidata Analysis Services in modo interattivo  
  
-   Fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server**, **Analysis Services**e quindi **Distribuzione guidata**.  
  
     -oppure-  
  
-   Nella cartella **Projects[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] del progetto di ** fare doppio clic sul file *\<nome progetto\>*.asdatabase.  
  
    > [!NOTE]  
    >  Se non è possibile trovare il file *\<nome progetto \>*.asdatabase, provare a usare la funzionalità di ricerca e specificare \*.asdatabase.  
  
## Esecuzione della Distribuzione guidata Analysis Services al prompt dei comandi  
 La Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] può essere inoltre eseguita al prompt dei comandi. In tal caso, è necessario specificare il percorso completo del file con estensione .asdatabase ed eseguire la procedura guidata in una delle modalità indicate di seguito.  
  
 **Modalità file di risposte**  
 In modalità file di risposte è possibile modificare in modo interattivo i file di input originariamente generati al durante la creazione del progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. I file di input modificati vengono salvati tramite la procedura guidata prima di creare lo script di distribuzione XMLA. I file di input modificati diventano il nuovo punto di partenza per la successiva esecuzione della procedura guidata.  
  
 Per eseguire la procedura guidata in modalità file di risposte, usare l'opzione **\/a**.  
  
 **Modalità automatica**  
 In modalità non interattiva viene eseguita una distribuzione automatica invisibile all'utente basata sulle informazioni incluse nei file di input.  
  
 Per eseguire la procedura guidata in modalità non interattiva, usare l'opzione **\/s**. Quando si esegue la procedura guidata in modalità non interattiva, i messaggi vengono inviati alla console o a un file di log, se presente.  
  
 **Modalità output**  
 In modalità output viene generato uno script di distribuzione XMLA da eseguire successivamente, basato sui file di input.  
  
 Per eseguire la procedura guidata in modalità output, usare l'opzione **\/o** e specificare il nome di un file di output.  
  
 Per altre informazioni sulle opzioni della riga di comando, vedere [Distribuire soluzioni di modelli con l'utilità di distribuzione](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md).  
  
 Nella procedura seguente viene illustrato come eseguire la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] al prompt dei comandi.  
  
#### Per eseguire la Distribuzione guidata Analysis Services al prompt dei comandi  
  
1.  Aprire un prompt dei comandi e passare alla cartella C:\\Programmi \(x86\)\\Microsoft SQL Server\\120\\Tools\\Binn\\ManagementStudio  
  
2.  Digitare **Microsoft.AnalysisServices.Deployment.exe** seguito dalle opzioni corrispondenti alla modalità in cui si desidera eseguire la procedura guidata.  
  
## Vedere anche  
 [Informazioni sullo script di distribuzione di Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)   
 [Deploy Model Solutions Using the Deployment Wizard](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)  
  
  