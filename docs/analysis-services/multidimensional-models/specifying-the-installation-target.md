---
title: "Impostazione della destinazione di installazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "file di input [Analysis Services]"
  - "destinazioni di installazione [Analysis Services]"
  - "distribuzioni di Analysis Services, destinazioni di installazione"
  - "Distribuzione guidata Analysis Services, destinazioni di installazione"
  - "distribuzione [Analysis Services], destinazioni di installazione"
  - "modifica di destinazioni di installazione"
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: 35
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Impostazione della destinazione di installazione
  La Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] legge le informazioni sulla destinazione di installazione dal file \<*nome progetto*>.deploymenttargets. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crea questo file quando si compila il progetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usa il database e il server specificati nella pagina **Distribuzione** della finestra di dialogo **Pagine delle proprietà** di *\<nome progetto>* per creare il file \<*nome progetto*>.targets.  
  
## Modifica della destinazione di installazione per la distribuzione  
 In alcuni casi potrebbe essere necessario distribuire un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] su un database o un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diversi da quelli specificati nella pagina **Distribuzione**. Potrebbe essere utile ad esempio distribuire il progetto su un server di prova prima della distribuzione e successivamente distribuire il progetto su un server di produzione dopo il completamento delle prove. Quando il progetto è completato e testato, potrebbe essere opportuno distribuirlo su più server di produzione in un cluster con bilanciamento del carico di rete o su un server dell'area di gestione temporanea e un server di produzione.  
  
 Per distribuire un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] su un database o un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] diversi, è possibile modificare la destinazione di installazione nel file di input utilizzando uno dei metodi descritti nella procedura seguente.  
  
#### Per modificare la destinazione di installazione dopo la generazione dei file di input.  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo interattivo. Nella pagina **Destinazione installazione**, specificare una nuova destinazione per il database e l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
     -oppure-  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso il prompt dei comandi e impostarla in modo che venga eseguita in modalità file di risposte. Per altre informazioni sulla modalità file di risposte, vedere [Esecuzione della distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     -oppure-  
  
-   Modificare il file \<*nome progetto*>.deploymenttargets usando un editor di testo.  
  
## Vedere anche  
 [Impostazione delle opzioni di distribuzione dei ruoli e delle partizioni](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)   
 [Definizione delle impostazioni di configurazione per la distribuzione di soluzioni](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)   
 [Impostazione delle opzioni di elaborazione](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  