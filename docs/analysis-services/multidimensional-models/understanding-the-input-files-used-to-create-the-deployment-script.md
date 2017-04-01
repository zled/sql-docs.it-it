---
title: "Informazioni sui file di input utilizzati per creare uno script di distribuzione | Microsoft Docs"
ms.custom: ""
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
  - "file di input [Analysis Services]"
  - "Distribuzione guidata Analysis Services, script"
  - "distribuzione [Analysis Services], file di input"
  - "Distribuzione guidata Analysis Services, file di input"
  - "script [Analysis Services], distribuzione"
  - "distribuzioni Analysis Services, file di input"
  - "modifica di file di input"
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Informazioni sui file di input utilizzati per creare uno script di distribuzione
  Quando si compila un progetto di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] genera file XML per il progetto. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] inserisce questi file XML nella cartella di output del progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per impostazione predefinita l'output si trova nella cartella \\Bin. Nella tabella seguente vengono elencati i file XML creati da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
|File XMLA|Description|  
|---------------|-----------------|  
|\<*nome progetto*\>.asdatabase|Contiene le definizioni dichiarative per tutti gli oggetti [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenuti nel progetto.|  
|\<*nome progetto*\>.deploymenttargets|Contiene il nome dell'istanza [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e del database in cui verranno creati gli oggetti [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|\<*nome progetto*\>.configsettings|Contiene le impostazioni specifiche all'ambiente, quali le informazioni sulla connessione all'origine dati e i percorsi di archiviazione degli oggetti. Le impostazioni contenute in questo file hanno la priorità sulle impostazioni contenute nel file \<*nome progetto*\>.asdatabase.|  
|\<*nome progetto*\>.deploymentoptions|Contiene le opzioni di distribuzione, come ad esempio se la distribuzione è transazionale o se gli oggetti distribuiti vanno elaborati dopo la distribuzione.|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] non archivia mai le password nei file di progetto.  
  
## Modifica del file di input  
 Modificando i valori contenuti nei file di input o i valori recuperati dai file di input, è possibile modificare la destinazione di distribuzione, le impostazioni di configurazione e le opzioni di distribuzione senza dover modificare l'intero file \<*nome progetto*\>.asdatabase \(o un intero file script XMLA qualora sia stato generato uno script da un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esistente\). La possibilità di modificare singoli file facilita la creazione di script di distribuzione diversi per vari scopi.  
  
 Gli argomenti seguenti illustrano come modificare valori nei vari file di input:  
  
-   [Impostazione della destinazione di installazione](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)  
  
-   [Impostazione delle opzioni di distribuzione dei ruoli e delle partizioni](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)  
  
-   [Definizione delle impostazioni di configurazione per la distribuzione di soluzioni](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)  
  
-   [Impostazione delle opzioni di elaborazione](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
## Vedere anche  
 [Esecuzione della Distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Informazioni sullo script di distribuzione di Analysis Services](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)  
  
  