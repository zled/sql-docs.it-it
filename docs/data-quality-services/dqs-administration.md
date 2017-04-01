---
title: "Amministrazione DQS | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "amministrazione dqs"
  - "amministrazione"
  - "DQS, amministrazione"
ms.assetid: 9940ef5d-f6f6-4dec-9414-1077a4d7f12b
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 21
---
# Amministrazione DQS
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) consente di amministrare e gestire varie attività DQS eseguite su [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], configurare le proprietà a livello di server correlate alle attività DQS, configurare le impostazioni del servizio dati di riferimento e configurare le impostazioni di log DQS. Queste attività vengono eseguite tramite il **amministrazione** funzionalità [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. In base all'accesso di sicurezza (ruolo) di cui si dispone in DQS, l'accesso a determinate funzioni in quest'area può essere concesso o negato.  
  
 Oltre che per queste attività di amministrazione, in questo argomento vengono fornite informazioni anche per un'attività amministrativa, il backup e ripristino di database DQS, che non viene eseguita utilizzando il [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
 La funzionalità di amministrazione nel [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] offre i vantaggi seguenti:  
  
-   Consente agli amministratori dei dati di eseguire il monitoraggio di varie attività DQS su un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] da un [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
-   Consente agli amministratori DQS di monitoraggio delle attività DQS su un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] da un [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], e *terminare* un'attività in esecuzione o *arrestare* un processo in esecuzione all'interno di un'attività, se necessario.  
  
-   Configurare le impostazioni del servizio dati di riferimento, ad esempio l'impostazione della connettività con Windows Azure Marketplace e la gestione di provider del servizio dati di riferimento diretti.  
  
-   Configurare valori soglia per le attività di pulizia e di corrispondenza.  
  
-   Abilitare/disabilitare notifiche nel [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
-   Configurare la registrazione in base al livello di gravità degli eventi.  
  
##  <a name="AdminUsingClent"></a> Attività di amministrazione tramite il client Data Quality  
 Queste attività vengono eseguite utilizzando il **amministrazione** funzionalità [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
### Monitoraggio attività  
 Il **Monitoraggio attività di** nella schermata [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] Visualizza informazioni dettagliate su ogni attività eseguita su un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]. Questa schermata viene utilizzata principalmente dall'amministratore dei dati per eseguire un monitoraggio di alto livello di tutte le attività eseguite sul [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] a cui è connessa l'applicazione [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Questa schermata non consente il monitoraggio a livello di sistema. Inoltre, questa schermata consente agli amministratori DQS di controllare un'attività o un processo all'interno di un'attività terminando un'attività in esecuzione o arrestando un processo in esecuzione all'interno di un'attività, se necessario. Vengono visualizzati i dati per l'individuazione delle informazioni, la gestione del dominio, i criteri di corrispondenza, la pulizia, la corrispondenza e la pulizia basata su SQL Server Integration Services (SSIS).  
  
### Configurazione  
 Il **configurazione** nella schermata [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] consente all'amministratore DQS di effettuare le operazioni seguenti:  
  
-   **Dati di riferimento**: configurare provider del servizio dati di riferimento: provider di servizi di Windows Azure Marketplace o dati di riferimento diretto. Dopo avere configurato i provider del servizio dati di riferimento, è possibile eseguire il mapping di un dominio singolo/composito ai dati di riferimento durante l'attività di gestione del dominio in una Knowledge Base, quindi utilizzare la stessa Knowledge Base per l'attività di pulizia in un progetto Data Quality. È inoltre possibile specificare le impostazioni proxy per la connessione a Internet per utilizzare Windows Azure Marketplace.  
  
-   **Impostazioni generali**: specificare i valori di soglia per la pulizia dei dati e corrispondenza dei dati e se si desidera abilitare le notifiche per l'analisi in [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Questi valori soglia vengono utilizzati da DQS durante le attività di pulizia assistita da computer e di corrispondenza in un progetto Data Quality.  
  
-   **Impostazioni di log**: I file di log in DQS registrare le attività eseguite in DQS e sono utili per il rilevamento di problemi operativi durante la manutenzione e risoluzione dei problemi. È possibile filtrare i messaggi che si desidera registrare per varie funzionalità DQS (gestione del dominio, individuazione delle informazioni, pulizia, corrispondenza e servizi dati di riferimento) e moduli DQS in base al livello di gravità degli eventi.  
  
> [!NOTE]  
>  Il **configurazione** schermata è disponibile solo per gli utenti che dispongono del ruolo dqs_administrator nel database DQS_MAIN.  
  
##  <a name="AdminOutsideClient"></a> Attività di amministrazione esterne al client Data Quality  
 Vi sono attività che vengono eseguite esternamente al client Data Quality:  
  
-   **Eseguire il backup e ripristino di database DQS**: il backup e ripristino dei database DQS è uguale a backup e ripristino dei database di SQL Server con alcune considerazioni specifiche di DQS.  
  
-   **Scollegare e collegare i database DQS**: I passaggi per scollegare e collegare i database DQS è uguale allo scollegamento e collegamento di un database di SQL Server con alcune considerazioni specifiche di DQS.  
  
 Per ulteriori informazioni, vedere [gestire database DQS](../data-quality-services/manage-dqs-databases.md).  
  
## Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene descritto come eseguire il monitoraggio delle attività in DQS.|[Monitorare le attività DQS](../data-quality-services/monitor-dqs-activities.md)|  
|Viene descritto come configurare le impostazioni dei dati di riferimento in DQS.|[Configure DQS to Use Reference Data](../data-quality-services/configure-dqs-to-use-reference-data.md)|  
|Viene descritto come configurare valori soglia per le attività di pulizia e di corrispondenza.|[Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md)|  
|Viene descritto come abilitare o disabilitare le notifiche in DQS.|[Enable or Disable Profiling Notifications in DQS](../data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md)|  
|Viene descritto come configurare la registrazione DQS in base al livello di gravità degli eventi.|[Configure Severity Levels for DQS Log Files](../data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|Viene descritto come configurare le impostazioni avanzate per la registrazione DQS.|[Configurare le impostazioni avanzate per i file di log DQS](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
|Viene descritto come eseguire il backup e il ripristino di database DQS.|[Backup e ripristino di database DQS](../data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|Viene descritto come scollegare e collegare i database DQS.|[Detaching and Attaching DQS Databases](../data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## Vedere anche  
 [Servizi dati di riferimento in DQS](../data-quality-services/reference-data-services-in-dqs.md)   
 [Gestire i file di log DQS](../data-quality-services/manage-dqs-log-files.md)   
 [Gestire i database DQS](../data-quality-services/manage-dqs-databases.md)  
  
  