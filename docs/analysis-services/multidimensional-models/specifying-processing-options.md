---
title: "Impostazione delle opzioni di elaborazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "distribuzioni di Analysis Services, opzioni di elaborazione"
  - "file di input [Analysis Services]"
  - "distribuzione [Analysis Services], opzioni di elaborazione"
  - "modifica di opzioni di elaborazione"
  - "Distribuzione guidata Analysis Services, opzioni di elaborazione"
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
caps.latest.revision: 32
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Impostazione delle opzioni di elaborazione
  La Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] legge le opzioni di elaborazione dal file \<*project name*>.deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crea questo file quando si compila il progetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usa le opzioni di elaborazione specificate nella pagina **Distribuzione** della finestra di dialogo **Pagine delle proprietà** di *\<project name>* per creare il file \<*project name*>.deploymentoptions.  
  
## Esame delle opzioni di elaborazione per la distribuzione  
 Il file \<*project name*>.deploymentoptions comprende le impostazioni di configurazione seguenti:  
  
-   **Metodo di elaborazione** Questa impostazione determina se gli oggetti distribuiti vengono elaborati dopo la distribuzione e il tipo di elaborazione a cui verranno sottoposti. Sono previste tre opzioni di elaborazione:  
  
    -   Elaborazione predefinita (impostazione predefinita)  
  
    -   Elaborazione completa  
  
    -   Nessuno  
  
-   **Opzioni tabella writeback** Se il writeback è attivato nel progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], questa impostazione stabilisce come verrà gestito. Sono previste tre opzioni per la tabella writeback:  
  
    -   Per impostazione predefinita, se esiste una tabella writeback essa verrà utilizzata. Se non esiste alcuna tabella writeback, ne verrà creata una nuova.  
  
    -   Se la tabella writeback esiste già, non potrà essere portata a termine la distribuzione. Se non esiste alcuna tabella writeback, ne verrà creata una nuova.  
  
    -   Anche se dovesse esistere già una tabella writeback, ne verrà creata una nuova. In questo caso, Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] elimina ogni eventuale tabella esistente e la sostituisce con una nuova tabella writeback.  
  
-   **Distribuzione transazionale** Questa impostazione stabilisce se la distribuzione delle modifiche dei metadati e dei comandi di elaborazione viene eseguita attraverso una singola transazione o in transazioni separate.  
  
    -   Se questa opzione è impostata su **True** (impostazione predefinita), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuisce tutte le modifiche dei metadati e tutti i comandi di elaborazione attraverso una singola transazione.  
  
    -   Se invece questa opzione è impostata su **False**, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuisce le modifiche dei metadati attraverso una singola transazione e distribuisce ogni comando di elaborazione in transazioni separate.  
  
## Modifica delle opzioni di elaborazione per la distribuzione  
 Potrebbe essere necessario distribuire il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usando opzioni di elaborazione diverse da quelle archiviate nel file \<*project name*>.deploymentoptions. Potrebbe ad esempio essere preferibile elaborare tutti gli oggetti in modo completo o elaborarli utilizzando l'opzione di elaborazione predefinita o infine non elaborarli affatto. Se i cubi o le dimensioni sono abilitati per la scrittura, è possibile specificare se verrà utilizzata una tabella writeback nuova o preesistente.  
  
 Per modificare le opzioni di elaborazione da utilizzare durante la distribuzione, è possibile modificare o ricompilare il progetto, oppure è possibile modificare le opzioni di elaborazione nel file di input utilizzando uno dei metodi descritti nella procedura seguente.  
  
#### Per modificare le opzioni di elaborazione dopo la generazione dei file di input  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo interattivo. Nella pagina **Opzioni di elaborazione** specificare le opzioni di elaborazione per il progetto da distribuire.  
  
     -oppure-  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso il prompt dei comandi e impostarla in modo che venga eseguita in modalità file di risposte. Per altre informazioni sulla modalità file di risposte, vedere [Esecuzione della Distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).
  
  
     -oppure-  
  
-   Modificare il file \<*project name*>.deploymentoptions usando un editor di testo.  
  
## Vedere anche  
 [Impostazione della destinazione di installazione](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)   
 [Impostazione delle opzioni di distribuzione dei ruoli e delle partizioni](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)   
 [Definizione delle impostazioni di configurazione per la distribuzione di soluzioni](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)  
  
  