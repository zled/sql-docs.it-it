---
title: "Utilizzare un&#39;origine dei dati esterna per i dati del Sottoscrittore (sottoscrizione guidata dai dati) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origini dei dati dei Sottoscrittori [Reporting Services]"
  - "sottoscrizioni [Reporting Services], origini dati esterne"
  - "sottoscrizioni basate su query [Reporting Services]"
  - "origini dei dati esterne [Reporting Services]"
  - "sottoscrizioni guidate dai dati"
  - "origini dati [Reporting Services], sottoscrizioni"
ms.assetid: 1cade8ec-729c-4df8-a428-e75c9ad86369
caps.latest.revision: 43
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 43
---
# Utilizzare un&#39;origine dei dati esterna per i dati del Sottoscrittore (sottoscrizione guidata dai dati)
  In una sottoscrizione guidata dai dati i dati di sottoscrizione dinamici vengono ottenuti tramite una query o un comando che consente di recuperare i dati da un'origine dei dati esterna. I dati di sottoscrizione possono essere recuperati da qualsiasi origine dei dati supportata che soddisfi i requisiti per l'elaborazione della sottoscrizione guidata dai dati. La sintassi della query o del comando deve essere valida per un'estensione per l'elaborazione dati installata con il server di report.  
  
## Requisiti per l'elaborazione dati  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa le estensioni per l'elaborazione dei dati per recuperare i dati di sottoscrizione. I tipi di origine dei dati consigliati sono i seguenti:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database relazionali  
  
-   database Oracle  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] origini dati di data mining e multidimensionali  
  
-   Origini dei dati XML  
  
     Quando si utilizza l'estensione per l'elaborazione dati XML per i dati del Sottoscrittore, aumentare le impostazioni di timeout per le query nella sottoscrizione. Per i valori di timeout per le query, nell'estensione per l'elaborazione dati XML vengono utilizzati i millisecondi anziché i secondi. Se non si aumenta il valore di timeout, la sottoscrizione potrebbe non riuscire a causa di tempi di elaborazione non sufficienti.  
  
     Quando si configura la connessione all'origine dei dati del Sottoscrittore, evitare di usare l'opzione **Credenziali non richieste**. Quando si utilizza l'estensione per l'elaborazione dati XML per recuperare i dati di sottoscrizione in fase di esecuzione è consigliabile utilizzare le credenziali archiviate.  
  
 Potrebbe essere possibile utilizzare altri tipi di origine dei dati supportati, ma il loro funzionamento non è garantito. I tipi di origine dei dati seguenti, ad esempio, non possono essere utilizzati per i dati del Sottoscrittore:  
  
-   Database SAP Netweaver BI  
  
-   Modelli di report  
  
 Se si ha un'estensione per l'elaborazione dati personalizzata che si vuole usare nelle sottoscrizioni guidate dai dati, è necessario che siano implementate le interfacce <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> e <xref:Microsoft.ReportingServices.DataProcessing.IDataReader>. L'estensione per l'elaborazione dati deve supportare l'esecuzione di query sul solo schema. Questo tipo di query è utilizzato per recuperare i metadati delle colonne in fase di progettazione, per consentire agli utenti di eseguire il mapping tra le colonne e le opzioni di recapito e i parametri del report nella definizione della sottoscrizione. L'esecuzione di query sul solo schema avviene in una fase iniziale, durante la definizione della sottoscrizione.  
  
## Requisiti per le query  
 Quando si crea una query per recuperare i dati di sottoscrizione, tenere presente quanto segue:  
  
-   È possibile creare una sola query per la sottoscrizione.  
  
-   La query deve restituire tutti i valori che si desidera utilizzare per le opzioni di recapito e per specificare i parametri del report.  
  
-   Tramite il server di report viene creato un recapito di report per ogni riga del set di risultati. Se il set di risultati è costituito da trecento righe, tramite il server di report verrà eseguito un tentativo di recapitare trecento report.  
  
## Impostazione di opzioni di recapito tramite dati di un database del Sottoscrittore  
 È possibile utilizzare i dati del database del Sottoscrittore per personalizzare le opzioni di recapito per ogni destinatario. Le opzioni disponibili sono determinate dal tipo di estensione per il recapito in uso. Se si utilizza l'estensione per il recapito tramite posta elettronica del server di report, la query dovrebbe contenere un alias di posta elettronica per ogni sottoscrittore. Se si utilizza un recapito alla condivisione file, i dati del Sottoscrittore devono includere valori che possano essere utilizzati per creare file di report specifici del Sottoscrittore o per offrire una destinazione per il recapito. Per altre informazioni, vedere [Recapito tramite posta elettronica in Reporting Services](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md).  
  
## Passaggio di valori dei parametri dal database del Sottoscrittore al report  
 Se si sta creando una sottoscrizione guidata dai dati per un report con parametri, è possibile fornire valori dei parametri variabili per personalizzare l'output di ogni report. Ad esempio, un database del Sottoscrittore potrebbe contenere numeri di identificazione, date di assunzione, titoli professionali e ubicazioni degli uffici dei dipendenti, tutte informazioni utilizzabili per filtrare i dati dei report. Se il report accetta parametri basati su queste o altre colonne di dati disponibili, è possibile eseguire il mapping di ogni parametro alla colonna appropriata.  
  
 Quando si esegue il mapping dei campi del Sottoscrittore ai parametri del report, verificare che i tipi di dati e la lunghezza delle colonne siano compatibili. Nel caso siano presenti tipi di dati non corrispondenti si verificherà un errore durante l'elaborazione della sottoscrizione. Per altre informazioni sull'uso di dati del sottoscrittore in un report con parametri, vedere [Creare una sottoscrizione guidata dai dati &#40;esercitazione su SSRS&#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md).  
  
## Modifica dell'origine dei dati del sottoscrittore  
 Le modifiche all'origine dei dati del sottoscrittore descritte di seguito possono impedire l'esecuzione della sottoscrizione:  
  
-   Rimozione di colonne cui si fa riferimento nella sottoscrizione.  
  
-   Modifica della struttura della tabella dell'origine dei dati.  
  
-   Modifica del tipo di dati e altre proprietà della colonna.  
  
 Se si apporta una qualsiasi di queste modifiche, sarà necessario aggiornare la sottoscrizione.  
  
## Vedere anche  
 [Come creare, modificare ed eliminare le sottoscrizioni guidate dai dati](../../reporting-services/subscriptions/create-modify-and-delete-data-driven-subscriptions.md)   
 [Sottoscrizioni guidate dai dati](../../reporting-services/subscriptions/data-driven-subscriptions.md)   
 [Sottoscrizioni e recapito &#40;Reporting Services&#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)  
  
  