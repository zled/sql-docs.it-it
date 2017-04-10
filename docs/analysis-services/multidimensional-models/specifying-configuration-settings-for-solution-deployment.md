---
title: "Definizione delle impostazioni di configurazione per la distribuzione di soluzioni | Microsoft Docs"
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
  - "Distribuzione guidata Analysis Services, impostazioni di configurazione"
  - "file di input [Analysis Services]"
  - "opzioni di configurazione [Analysis Services]"
  - "distribuzioni di Analysis Services, impostazioni di configurazione"
  - "distribuzione [Analysis Services], impostazioni di configurazione"
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Definizione delle impostazioni di configurazione per la distribuzione di soluzioni
  La Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] legge le opzioni di partizione e di distribuzione dei ruoli usate nello script di distribuzione dal file \<*nome progetto*>.configsettings. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] crea questo file quando si compila il progetto [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usa le impostazioni di configurazione del progetto corrente per creare il file \<*nome progetto*>.configsettings.  
  
## Esame delle opzioni di configurazione per la distribuzione  
 Nel file \<*nome progetto*>.configsettings vengono archiviate le impostazioni di configurazione seguenti:  
  
-   **Stringhe di connessione origine dati** Stringhe di connessione per ciascuna origine dati basate sui valori specificati nel progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. L'ID utente e la password vengono sempre rimossi dalla stringa di connessione prima che il resto della stringa venga archiviato nel file. Se invece viene eseguita la distribuzione direttamente in un'istanza di Analysis Services, è possibile aggiungere le informazioni appropriate relative a ID utente e password all'interno della Distribuzione guidata per garantire l'elaborazione corretta del database di distribuzione. Queste informazioni di connessione non vengono archiviate nello script di distribuzione eventualmente salvato dalla Distribuzione guidata.  
  
-   **Impostazioni di rappresentazione** Questa impostazione definisce il nome utente usato da [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per eseguire istruzioni in ciascuna origine dati. Se non è stato specificato alcun account di rappresentazione, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verrà utilizzato l'account di accesso per eseguire le istruzioni. Se all'account di accesso [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene concesso l'accesso diretto all'origine dati, tutti gli amministratori del database di tutti i database dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] avranno accesso all'origine dati attraverso l'account di accesso. Se vengono specificati un account utente e una password, tali informazioni vengono sempre rimosse prima che le impostazioni di rappresentazione vengano archiviate nel file. Se invece viene eseguita la distribuzione direttamente in un'istanza di Analysis Services, è possibile aggiungere le informazioni appropriate relative a ID utente e password all'interno della Distribuzione guidata per garantire l'elaborazione corretta del database di distribuzione. Queste impostazioni di rappresentazione non vengono archiviate nello script di distribuzione eventualmente salvato dalla Distribuzione guidata.  
  
-   **File di log degli errori di chiave** Questa impostazione definisce il nome e il percorso del file di log degli errori di chiave di ciascun cubo, gruppo di misure, partizione e dimensione del database.  
  
-   **Percorsi di archiviazione** Questa impostazione definisce la posizione di archiviazione di ciascun cubo, gruppo di misure e partizione del database. Se non è stato specificato alcun valore per un oggetto, Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilizza la posizione predefinita per tale oggetto. Le partizioni utilizzano ad esempio la posizione del gruppo di misure, i gruppi di misure utilizzano la posizione del cubo e i cubi utilizzano la posizione predefinita degli oggetti dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La posizione di archiviazione può essere un percorso locale o un percorso UNC (Universal Naming Convention).  
  
-   **Server di report** Questa impostazione definisce il server di report e la posizione della cartella per ciascuna azione report definita in ciascun cubo del database.  
  
## Modifica delle impostazioni di configurazione per la distribuzione  
 In alcuni casi, potrebbe essere necessario distribuire il progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usando impostazioni di configurazione diverse da quelle archiviate nel file \<*nome progetto*>.configsettings. Potrebbe ad esempio essere preferibile modificare la stringa di connessione per una o più origini dati o specificare posizioni di archiviazione per particolari partizioni o gruppi di misure.  
  
 Per modificare la distribuzione di partizioni e ruoli in un progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è necessario modificare queste informazioni all'interno del file \<*nome progetto*>.configsettings, come descritto nella procedura seguente. Le impostazioni dei ruoli e delle partizioni non possono essere modificate all'interno del progetto perché nella finestra di dialogo **Impostazione proprietà di configurazione** *\<nome progetto>* di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] queste opzioni non sono visualizzate.  
  
> [!NOTE]  
>  Le impostazioni di configurazione possono essere applicate a tutti gli oggetti o solo ai nuovi oggetti creati. Le impostazioni di configurazione possono essere applicate solo ai nuovi oggetti creati quando si distribuiscono oggetti aggiuntivi a un database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuito precedentemente e non si desidera sovrascrivere gli oggetti esistenti. Per specificare se le impostazioni di configurazione vanno applicate a tutti gli oggetti o solo ai nuovi oggetti creati, è necessario impostare opportunamente questa opzione nel file \<*nome progetto*>.deploymentoptions. Per altre informazioni, vedere [Impostazione delle opzioni di distribuzione dei ruoli e delle partizioni](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md).  
  
#### Per modificare le opzioni di configurazione dopo la generazione dei file di input  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo interattivo e specificare le impostazioni di configurazione per gli oggetti da distribuire nella pagina **Impostazione proprietà di configurazione**.  
  
     -oppure-  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso il prompt dei comandi e impostarla in modo che venga eseguita in modalità file di risposte. Per altre informazioni sulla modalità file di risposte, vedere [Esecuzione della Distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     -oppure-  
  
-   Modificare il file \<*nome progetto*>.configsettings usando un editor di testo.  
  
## Vedere anche  
 [Impostazione della destinazione di installazione](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)   
 [Impostazione delle opzioni di distribuzione dei ruoli e delle partizioni](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)   
 [Impostazione delle opzioni di elaborazione](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  