---
title: "Configurare livelli di gravit&#224; per i file di log DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dqs.admin.config.log.f1"
helpviewer_keywords: 
  - "severity levels"
  - "log files,severity levels"
  - "dqs log files,severity levels"
  - "logging,severity levels"
  - "configurare i livelli di gravità"
ms.assetid: 66ffcdec-4bf7-4dd5-a221-fd9baefeeef4
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Configurare livelli di gravit&#224; per i file di log DQS
  In questo argomento viene descritto come configurare i livelli di gravità per le varie attività e i vari moduli di [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) tramite il [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. I livelli di gravità definiscono l'intensità degli eventi che si verificano in DQS. Gli eventi DQS dispongono dei livelli di gravità seguenti, in ordine di gravità decrescente:  
  
-   **Errore irreversibile**: errori di run-time critici che potrebbero provocare risultati gravi/imprevisti.  
  
-   **Errore**: altri errori di run-time.  
  
-   **Avviso**: avviso sugli eventi che potrebbero generare un errore.  
  
-   **Informazioni**: informazioni sugli eventi generali che non sono errori o avvisi. Ad esempio, un processo DQS avviato.  
  
-   **Eseguire il debug**: (verbose) informazioni dettagliate sull'evento.  
  
 Quando si configurano i livelli di gravità per varie attività e i vari moduli DQS, si filtrano le informazioni che si desidera registrare e scrivere nel file di log DQS per la rispettiva attività o modulo DQS. Ad esempio, se si imposta il livello di gravità di un'attività DQS su **Avvisa**, avviso e solo superiore verranno registrati i messaggi di gravità (errore ed errore irreversibile) associati all'attività DQS.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per configurare le impostazioni di gravità del log, è necessario disporre del ruolo dqs_administrator per il database DQS_MAIN.  
  
##  <a name="ConfigureActivity"></a> Configurare i livelli di gravità a livello di attività  
 In DQS è possibile configurare le impostazioni di gravità del log per le attività seguenti: gestione del dominio, individuazione delle informazioni, criteri di corrispondenza, pulizia dei dati, corrispondenza dei dati e servizi dati di riferimento. A tale scopo, procedere come indicato di seguito:  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Eseguire l'applicazione Client Data Quality](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  Nella schermata iniziale del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] fare clic su **Configurazione**.  
  
3.  Successivamente, fare clic su di **le impostazioni del registro** scheda. Le attività DQS seguenti sono elencate per il quale è possibile selezionare un livello di gravità: **Domain Management**, **l'individuazione delle informazioni**, **progetto di pulizia (es: Servizi Desktop remoto)**, **criteri di corrispondenza e progetto corrispondente**, e **RDS**.  
  
4.  Selezionare il livello di gravità che si desidera registrare per un'attività DQS. È possibile selezionare uno tra i valori seguenti: **Errore irreversibile**, **Errore**, **Avviso**, **Informazioni**e **Debug**. Ad esempio, se si desidera solo irreversibili messaggi scritti nel file di log DQS per l'attività individuazione informazioni, selezionare **errore irreversibile** nell'elenco a discesa contro la **l'individuazione delle informazioni** attività.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, è selezionato **Errore** per ognuna delle attività. Ciò significa che i messaggi di errore ed errore irreversibile verranno scritti nei file di log DQS per ogni attività per impostazione predefinita.  
  
5.  Scegliere **Chiudi**.  
  
##  <a name="ConfigureModule"></a> Configurare i livelli di gravità a livello di modulo (impostazione avanzata)  
 La sezione **Avanzate** della scheda **Impostazioni log** consente di configurare le impostazioni di gravità del log a livello di modulo. I moduli sono assembly di sistema DQS che implementano varie funzionalità all'interno di una funzionalità in DQS. Ad esempio, l'attività di gestione del dominio contiene varie funzionalità quali la definizione di regole di dominio, la definizione di condizioni della regola, la definizione di regole tra domini per i domini compositi e così via.  
  
 Talvolta, il livello di granularità a livello di attività non è sufficiente. Può essere necessario esaminare un problema che si è verificato in un particolare modulo all'interno di un'attività. È possibile pertanto configurare i livelli di gravità del log a livello di modulo per isolare e tenere traccia del problema con maggiore precisione.  
  
 L'impostazione di gravità del log specificata a livello di attività determina l'impostazione di gravità del log di tutti i moduli che costituiscono l'attività. Tuttavia, in caso di conflitto tra le impostazioni di gravità del log a livello di attività e a livello di modulo, vengono considerate le impostazioni di gravità a livello di modulo.  
  
> [!NOTE]  
>  -   Per impostazione predefinita, il modulo **Microsoft.Ssdqs.Core.Startup** viene preconfigurato nella sezione **Avanzate** con il livello di gravità impostato su **Informazioni**. Ciò consente di registrare gli eventi con il livello di gravità Informazioni e con un livello maggiore (Avviso, Errore ed Errore irreversibile) correlati all'avvio e all'arresto dei servizi DQS.  
> -   È consigliabile configurare i livelli di gravità del log a livello di modulo solo se si è un utente DQS avanzato con familiarità con gli assembly di sistema DQS.  
  
 Per configurare i livelli di gravità del log a livello di modulo:  
  
1.  Nella scheda **Impostazioni log** fare clic sulla freccia in giù accanto ad **Avanzate** per visualizzare l'area.  
  
2.  Nella griglia visualizzata, selezionare un nome di modulo dall'elenco a discesa nel **modulo** colonna.  
  
3.  Successivamente, selezionare un livello di gravità per il modulo dall'elenco a discesa nel **gravità** colonna. È possibile selezionare uno tra i valori seguenti: **Errore irreversibile**, **Errore**, **Avviso**, **Informazioni**e **Debug**.  
  
     Ad esempio, all'interno dell'attività di gestione del dominio, è possibile impostare un livello di granularità diverso per la funzionalità di definizione di una regola di dominio rispetto all'attività di gestione del dominio selezionando il modulo **Microsoft.Ssdqs.DomainRules.Define** e selezionando un livello di gravità del log diverso. Analogamente, è possibile impostare un livello di granularità diverso per la funzionalità di regola tra domini selezionando il **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** modulo e selezionando un livello di gravità del log diverso.  
  
4.  Ripetere i passaggi 2 e 3 per altri moduli, se necessario. È inoltre possibile aggiungere o eliminare righe nella griglia facendo clic sulle icone **Aggiungi modulo** e **Rimuovi modulo** .  
  
5.  Scegliere **Chiudi**.  
  
## Vedere anche  
 [Configurare le impostazioni avanzate per i file di log DQS](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md)  
  
  