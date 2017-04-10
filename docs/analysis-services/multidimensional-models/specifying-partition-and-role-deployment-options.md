---
title: "Impostazione delle opzioni di distribuzione dei ruoli e delle partizioni | Microsoft Docs"
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
  - "partizioni [Analysis Services], opzioni di distribuzione"
  - "distribuzioni di Analysis Services, ruoli"
  - "distribuzioni di Analysis Services, partizioni"
  - "Distribuzione guidata Analysis Services, ruoli"
  - "Distribuzione guidata Analysis Services, partizioni"
  - "distribuzione [Analysis Services], ruoli"
  - "ruoli [Analysis Services], opzioni di distribuzione"
  - "distribuzione [Analysis Services], partizioni"
  - "modifica di distribuzioni di ruoli"
  - "modifica di distribuzioni di partizioni"
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Impostazione delle opzioni di distribuzione dei ruoli e delle partizioni
  La Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] legge le opzioni di distribuzione di partizione e ruoli dal file \<*nome progetto*>.deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crea questo file quando si compila il progetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usa le opzioni di partizione e di distribuzione dei ruoli del progetto corrente quando viene creato il file \<*nome progetto*>.deploymentoptions. Per altre informazioni sulle impostazioni di configurazione, vedere [Informazioni sui file di input utilizzati per creare uno script di distribuzione](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md).  
  
## Esame delle opzioni di distribuzione dei ruoli e delle partizioni  
 Il file \<*nome progetto*>.deploymentoptions comprende le opzioni seguenti:  
  
 **Opzioni di distribuzione delle partizioni**  
 Nel file \<*nome progetto*>.deploymentoptions viene specificato se le partizioni esistenti del database di destinazione vengono mantenute o vengono sovrascritte (impostazione predefinita). Se le partizioni esistenti vengono mantenute, verranno distribuite solo le nuove partizioni, e le partizioni e le progettazioni delle aggregazioni in tutti i gruppi di misure esistenti non saranno modificate.  
  
> [!NOTE]  
>  Se il gruppo di misure contenente la partizione viene eliminato, la partizione viene eliminata automaticamente.  
  
 **Opzioni di distribuzione dei ruoli**  
 Nel file \<*nome progetto*>.deploymentoptions viene specificata una delle seguenti opzioni di distribuzione dei ruoli:  
  
-   I ruoli e i membri di ruolo esistenti contenuti nel database di destinazione vengono mantenuti e vengono distribuiti solo i nuovi ruoli e membri di ruolo.  
  
-   Tutti i membri e ruoli esistenti contenuti nel database di destinazione vengono sostituiti dai ruoli e dai membri distribuiti.  
  
-   I ruoli e i membri di ruolo esistenti contenuti nel database di destinazione vengono mantenuti e non viene distribuito nessun nuovo ruolo.  
  
-   **Nota**Quando vengono mantenuti i ruoli e i membri esistenti, le autorizzazioni associate a tali ruoli vengono reimpostate su nessuna autorizzazione. Le autorizzazioni di sicurezza sono contenute negli oggetti da esse protetti, non nei ruoli di sicurezza a cui sono associate. Per ulteriori informazioni su come gestire tale comportamento utilizzando la Distribuzione guidata Analysis Services, vedere "Mantieni ruoli e membri" nella Microsoft Knowledge Base.  
  
## Modifica delle opzioni di distribuzione dei ruoli e delle partizioni  
 Potrebbe essere necessario distribuire il progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usando opzioni per ruoli e partizioni diverse da quelle archiviate nel file \<*nome progetto*>.deploymentoptions. Potrebbe ad esempio essere preferibile mantenere le partizioni, i ruoli e i membri di ruolo esistenti invece che sostituire tutte le partizioni, i ruoli e i membri come indicato nel file \<*nome progetto*>.deploymentoptions.  
  
 Per modificare la distribuzione di partizioni e ruoli in un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], non è possibile modificare le impostazioni delle partizioni e dei ruoli all'interno del progetto poiché queste opzioni non sono visualizzate nella finestra di dialogo *Pagine delle proprietà ***\<nome progetto>** di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Se si desidera modificare le opzioni di distribuzione dei ruoli e delle partizioni, è necessario modificare queste informazioni all'interno del file \<*nome progetto*>.deploymentoptions. La procedura seguente illustra come modificare le opzioni di distribuzione delle partizioni e dei ruoli all'interno del file \<*nome progetto*>.deploymentoptions.  
  
#### Per modificare la distribuzione delle partizioni o dei ruoli dopo la generazione dei file di input  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo interattivo e specificare nuove opzioni di distribuzione delle partizioni e dei ruoli nella pagina relativa alle **opzioni partizioni e ruoli della distribuzione**.  
  
     -oppure-  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso il prompt dei comandi e impostarla in modo che venga eseguita in modalità file di risposte. Per altre informazioni sulla modalità file di risposte, vedere [Esecuzione della Distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     -oppure-  
  
-   Aprire il file \<*nome progetto*>.deploymentoptions in un qualsiasi editor di testo e modificare manualmente le opzioni.  
  
## Vedere anche  
 [Impostazione della destinazione di installazione](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)   
 [Definizione delle impostazioni di configurazione per la distribuzione di soluzioni](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)   
 [Impostazione delle opzioni di elaborazione](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  