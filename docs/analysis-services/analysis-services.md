---
title: "Analysis Services | Microsoft Docs"
ms.date: "03/28/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
helpviewer_keywords: 
  - "Analysis Services, informazioni su Analysis Services - Dati multidimensionali"
  - "SSAS"
  - "Analysis Services"
  - "SQL Server Analysis Services, informazioni su Analysis Services - Dati multidimensionali"
  - "SQL Server Analysis Services"
  - "dati multidimensionali [Analysis Services]"
  - "SSAS, informazioni su Analysis Services - Dati multidimensionali"
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
caps.latest.revision: 60
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 60
---
# Analysis Services
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] è un motore di dati analitici online usato nel supporto decisionale e nell'analisi business che rende disponibili i dati analitici da usare nei report aziendali e nelle applicazioni client quali i report di Reporting Services, Excel, Power BI e altri strumenti di visualizzazione dei dati di terze parti.  
  
 Un tipico flusso di lavoro per [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] include la creazione di un modello di dati multidimensionale o tabulare, la distribuzione del modello come database in un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , l'elaborazione del database per caricarvi dati o metadati, l'impostazione di aggiornamento dei dati e l'assegnazione di autorizzazioni per consentire l'accesso ai dati dagli utenti finali. Quando è pronto, il modello di dati semantici multifunzione sarà accessibile a qualsiasi applicazione client che supporta [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] come origine dati.  
  
 I modelli vengono popolati con i dati dei sistemi di dati esterni, in genere data warehouse ospitati in un motore di database relazionale Oracle o SQL Server (i modelli tabulari supportano i tipi di origine dati aggiuntivi). I modelli specificano oggetti query, ad esempio cubi, ma specificano anche dimensioni che possono essere usate in più cubi, calcoli e indicatori KPI che incapsulano la logica di business e interazioni quali navigazione e comportamenti drill-through.  
 
## <a name="analysis-services-on-premises-and-in-the-cloud"></a>Analysis Services locale e nel cloud
Analysis Services è ora disponibile nel cloud come servizio di Azure. Attualmente in anteprima, Azure Analysis Services supporta modelli tabulari a livello di compatibilità 1200. DirectQuery, partizioni, sicurezza a livello di riga, relazioni bidirezionali e traduzioni sono tutte funzioni supportate. Per altre informazioni e per una prova gratuita, vedere [Azure Analysis Services](https://azure.microsoft.com/en-us/services/analysis-services/). 
  
## <a name="server-mode"></a>Modalità server  
 Quando si installa Analysis Services usando [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] Setup, durante la configurazione specificare una modalità server per l'istanza.  Ogni modalità include diverse funzionalità specifiche di una particolare soluzione di Analysis Services.  
  
-   **Modalità multidimensionale e di data mining** -Implementare costrutti di modellazione OLAP (cubi, dimensioni, misure).  
  
-   **Modalità tabulare** - Implementare costrutti di modellazione dei dati relazionali in memoria (modello, tabelle, colonne).  
  
     I modelli tabulari possono essere creati al livello di compatibilità predefinito 1200 per usare la funzionalità più recente o al livello di compatibilità 1103, che è meno recente. Esistono differenze significative tra i livelli di compatibilità. Per informazioni sul confronto dei livelli, vedere [Livello di compatibilità per i modelli tabulari in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md).  
  
-   **Modalità Power Pivot** - Implementare i modelli di dati [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ed Excel in SharePoint ([!INCLUDE[ssGemini](../includes/ssgemini-md.md)] per SharePoint è un motore dati di livello intermedio che carica, esegue query e aggiorna i modelli di dati ospitati in SharePoint).  
  
 Una singola istanza può essere configurata con un'unica modalità e non può essere modificata in un secondo momento.  È possibile installare più istanze con modalità diverse sullo stesso server, ma è necessario eseguire il programma di installazione e specificare le impostazioni di configurazione per ogni istanza.  
  
 Le funzionalità di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] variano in base all'edizione. Per altre informazioni, vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](../sql-server/edizioni-e-funzionalità-supportate-per-sql-server-2016.md) 
  
## <a name="authoring-solutions"></a>Creazione di soluzioni  
 Per creare un modello, usare SQL Server Data Tools (vedere [Strumenti e applicazioni usati in Analysis Services](../analysis-services/tools-and-applications-used-in-analysis-services.md)), scegliendo un modello di progetto tabulare o multidimensionale e di data mining. Il modello di progetto include cartelle per tutti gli oggetti necessari in un modello. È possibile usare le procedure guidate per creare la maggior parte degli elementi di base, ad esempio origini dati, viste origine dati, dimensioni, cubi e ruoli.  
  
## <a name="documentation-by-area"></a>Documentazione per area  
La documentazione per Analysis Services è organizzata in sezioni che corrispondono al tipo di progetto che si sta compilando. Per ulteriori informazioni su questa modalità o area funzionale, scegliere tra i seguenti collegamenti.  
   
 ![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola") [Novità](../analysis-services/what-s-new-in-analysis-services.md)  
  
 ![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola") [Confronto tra soluzioni tabulari e multidimensionali](../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola")[Modelli tabulari](../analysis-services/tabular-models/tabular-models-ssas.md)  
  
 ![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola")[Modelli multidimensionali](../analysis-services/multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola") [Data Mining](../analysis-services/data-mining/data-mining-ssas.md)  
  
 ![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola") [ Power Pivot per SharePoint](../analysis-services/power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
 ![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola") [Gestione di un'istanza di Analysis Services](../analysis-services/instances/analysis-services-instance-management.md)  
   
 ![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola") [Esercitazioni su Analysis Services](../analysis-services/analysis-services-tutorials-ssas.md)  
  
![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola") [Guida per gli sviluppatori (Analysis Services)](https://msdn.microsoft.com/library/bb500153(SQL.130).aspx)  
 
![Icona della cartella file piccola](../analysis-services/media/filefolder-small.png "Icona della cartella file piccola") [Guida di riferimento tecnico (SSAS)](../analysis-services/powershell/technical-reference-ssas.md)