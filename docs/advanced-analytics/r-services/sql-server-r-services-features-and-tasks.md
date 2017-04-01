---
title: "Caratteristiche e attivit&#224; di SQL Server R Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "05/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52ad3f10-6d24-477a-aeb6-110456b2ed1c
caps.latest.revision: 13
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 13
---
# Caratteristiche e attivit&#224; di SQL Server R Services
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] combina la potenza e flessibilità del linguaggio R open source con gli strumenti di livello aziendale per l'archiviazione e gestione, lo sviluppo del flusso di lavoro e creazione di report e visualizzazione. Supporta le esigenze dei professionisti di quattro diversi dati e gli scenari.  
  
## Esperti di dati: Analisi, modellazione e assegnazione di punteggi con R e SQL Server  
 Gli esperti di dati ha accesso a un'ampia gamma di strumenti per l'analisi dei dati e il Machine Learning, che comprende il noto Excel e piattaforme open source, fino a suite statistiche costose che richiedono conoscenze tecniche approfondite. Tra questi, [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre vantaggi esclusivi poiché consente agli esperti di dati di eseguire il pushing dei calcoli al database, evitando lo spostamento di dati e rispettando i criteri di sicurezza aziendali. In aggiunta, il codice R creato dagli esperti può facilmente essere distribuito nell'ambiente di produzione e chiamato dagli strumenti e dalle soluzioni in uso nell'azienda: applicazioni basate su database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , strumenti di creazione di report di Business Intelligence e dashboard. Usando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], l'esperto può distribuire e aggiornare qualsiasi soluzione di analisi rispettando i requisiti standard per la gestione dei dati aziendali, tra cui sicurezza, facilità di distribuzione, gestione e monitoraggio, nonché controllo dell'accesso.  
  
-   **Interfaccia utente familiare:**  Sviluppare e testare le soluzioni utilizzando l'ambiente di sviluppo R di propria scelta.  
  
-   **Elaborazione nel database:**  Eseguire il codice R e che i calcoli vengano effettuati su computer che ospita il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza. Questa operazione elimina la necessità di spostare i dati.  
  
-   **Prestazioni e scalabilità:**  Include scalabile pacchetti R e le API, in modo non è limitato dall'architettura di memoria associato a thread singolo di R. È possibile utilizzare con grandi set di dati e calcoli multithread, multi-core, più processi.  
    
-   **Portabilità del codice:**  Lo stesso codice R che viene eseguita sulle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati possono essere riutilizzati facilmente in altre origini dati, ad esempio Hadoop.  
  
 Per informazioni dettagliate sui concetti e attività correlate, vedere [l'esplorazione dei dati e la modellazione predittiva con R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).  
  
## Sviluppatori di applicazioni e database: distribuire le soluzioni R  
 Gli sviluppatori di database si occupano di integrare più tecnologie e raggruppare i risultati in modo che possano essere condivisi in tutta l'organizzazione. Lo sviluppatore di database collabora con sviluppatori di applicazioni, sviluppatori di SQL ed esperti di dati per progettare soluzioni, metodi di gestione dei dati consigliati, per architettare e distribuire le soluzioni. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre numerosi vantaggi agli sviluppatori che lavorano con gli esperti di dati:  
  
-   **Interagire con gli script R utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)].**  gli sviluppatori di report, gli analisti e gli sviluppatori di database possono richiamare gli script R chiamando le stored procedure di sistema. Se la soluzione utilizza le aggregazioni complesse o comporta grandi set di dati, è possibile impostare calcoli eseguire nel database oppure utilizzare una combinazione di R e [!INCLUDE[tsql](../../includes/tsql-md.md)], a seconda che offre le migliori prestazioni. La semplice integrazione con  [!INCLUDE[tsql](../../includes/tsql-md.md)] risulta particolarmente importante quando è necessario eseguire ripetutamente attività su grandi quantità di dati, ad esempio la generazione di punteggi di stima sui dati di produzione.  
  
     L'integrazione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] implica anche la possibilità di eseguire gli script R da qualsiasi applicazione che usa [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ad esempio, è facilmente possibile chiamare una stored procedure da un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report per richiamare script R e generare un grafico con le stime nel report.  
  
-   **Prestazioni e scalabilità:**  Sebbene il linguaggio R open source è noto per le limitazioni, il pacchetto RevoScaleR API fornite da [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] può operare su grandi set di dati e trarre vantaggio da più thread, multi-core, multiprocesso calcoli nel database.  
  
-   **Strumenti di sviluppo e gestione standard:**  Nessun strumenti aggiuntivi per amministrazione o distribuzione necessaria; tutti i processi R possono essere chiamati da richiamare una stored procedure. In aggiunta, lo stesso codice R che viene eseguito sui dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere riusato su altre origini dati, ad esempio Hadoop.  
  
 Per informazioni dettagliate sui concetti e attività correlate, vedere [operatività del codice R](../../advanced-analytics/r-services/operationalizing-your-r-code.md).  
  
## Amministratori di database: Gestire soluzioni di analisi avanzate  
 Gli amministratori di database devono integrare progetti e priorità in concorrenza all'interno di un singolo punto di contatto: il server di database. È necessario specificare l'accesso ai dati non solo per gli esperti, ma per un'ampia gamma di sviluppatori di report, analisti aziendali e fruitori dei dati aziendali, mantenendo l'integrità degli archivi dei dati operativi e dei report. Nell'organizzazione, l'amministratore di database è una parte fondamentale della compilazione e distribuzione di un'infrastruttura efficace per la scienza dei dati. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offre numerosi vantaggi all'amministratore di database che supporta il ruolo della scienza dei dati:  
  
-   **Sicurezza.**  L'architettura di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] mantiene i database protetto e isola l'esecuzione di sessioni R dall'operazione dell'istanza del database.  
  
     È possibile specificare gli utenti autorizzati a eseguire gli script R e assicurarsi che i dati utilizzati nei processi R viene gestiti utilizzando gli stessi ruoli di sicurezza definiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   **Affidabilità:**  le sessioni R vengono eseguite in un processo separato per garantire che il server continui a funzionare normalmente anche in caso di problemi della sessione R.  
  
-   **Governance delle risorse:**  È anche possibile tenere sotto controllo la quantità di risorse allocate al runtime di R, per evitare che calcoli di grande entità possano compromettere le prestazioni complessive del server.  
  
 Per informazioni dettagliate su concetti e attività correlate, vedere [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md).  
  
## Architetti e progettisti ETL: Creare flussi di lavoro integrati che si estendono su R e SQL Server  
 Gli ingegneri dei dati creano e compilano le soluzioni ETL. Gli architetti progettano le piattaforme di dati per soddisfare le esigenze aziendali in termini di concorrenza e completezza. Poiché [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è integrato con altri strumenti di Microsoft, ad esempio il business intelligence e stack di data warehouse, cloud dell'organizzazione e gli strumenti di mobilità e Hadoop, offre una gamma di vantaggi per i dati tecnico architetto di sistema che desiderano promuovere analisi avanzata dei dati.  
  
-   **Ampia gamma di strumenti di sviluppo conosciuti:**  Quando si sviluppano soluzioni R, usare [!INCLUDE[tsql](../../includes/tsql-md.md)] e stored procedure per popolare i set di dati, eseguire i processi R o ottenere stime di sistema. Gli strumenti della scienza dei dati non consentono più la progettazione di flussi di lavoro paralleli. Compilare le pipeline di dati nell'ambiente ormai familiare di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
     È necessario usare i dati nel cloud? Supporto per Data Factory di Azure e Database SQL di Azure rende più semplice trasformare e gestire i dati e origini di dati di utilizzo cloud nei flussi di lavoro semplicemente come quelle per le distribuzioni locali [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati.  
  
-   **Creazione e gestione dei flussi di lavoro:**  Pianificare i processi e creare flussi di lavoro che contiene gli script R, utilizzando stored procedure di sistema.  
  
 Per informazioni dettagliate sui concetti e attività correlate, vedere [creazione dei flussi di lavoro che usa R in SQL Server](../../advanced-analytics/r-services/creating-workflows-that-use-r-in-sql-server.md).  
  
## Vedere anche  
 [Introduzione a SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  