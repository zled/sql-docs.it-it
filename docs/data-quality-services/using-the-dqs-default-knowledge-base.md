---
title: "Utilizzo della Knowledge Base predefinita di DQS | Microsoft Docs"
ms.custom: ""
ms.date: "07/31/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
caps.latest.revision: 13
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 13
---
# Utilizzo della Knowledge Base predefinita di DQS
  In questo argomento viene descritta la knowledge base predefinita **dati DQS**, che viene installato con [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Si tratta di una Knowledge Base precompilata che contiene i domini seguenti:  
  
-   **Paese/area geografica**: contiene i nomi lunghi (nome ufficiale designato dal paese) e nomi brevi (nome comune utilizzato in elenchi, su mappe e così via), abbreviazione di due lettere, abbreviazione di tre lettere e codice di tre cifre per ogni posizione.  Il valore iniziale è impostato sul nome paese lungo.  
  
-   **Paese (tre lettere iniziali)**: contiene i nomi lunghi (nome ufficiale designato dal paese) e nomi brevi (nome comune utilizzato in elenchi, su mappe e così via), abbreviazione di due lettere, abbreviazione di tre lettere e codice di tre cifre per ogni posizione.  Il valore iniziale è impostato sull'abbreviazione paese di tre lettere.  
  
-   **Paese (due lettere iniziali)**: contiene i nomi lunghi (nome ufficiale designato dal paese) e nomi brevi (nome comune utilizzato in elenchi, su mappe e così via), abbreviazione di due lettere, abbreviazione di tre lettere e codice di tre cifre per ogni posizione.  Il valore iniziale è impostato sull'abbreviazione paese di due lettere.  
  
-   **US - provincie**: contiene un elenco di provincie US.  
  
-   **US - cognome**: contiene un elenco dei cognomi (cognomi) che si verificano 100 o più volte in Census 2000.  
  
-   **US - luoghi**: contiene un elenco di posizioni dei 50 stati, District of Columbia e Porto Rico estratti da Census 2010.  
  
-   **US - stato**: contiene il lungo (ufficiale) convenzionale nome e l'abbreviazione di due lettere per ogni stato negli Stati Uniti. Il valore iniziale è impostato sul nome stato convenzionale.  
  
-   **US-stato (intestazione di 2 lettere)**: contiene il lungo (ufficiale) convenzionale nome e l'abbreviazione di due lettere per ogni stato negli Stati Uniti. Il valore iniziale è impostato sull'abbreviazione di due lettere del nome dello stato.  
  
## Utilizzo della Knowledge Base predefinita  
 È possibile utilizzare la Knowledge Base DQS predefinita, i dati DQS, nei modi seguenti:  
  
-   Avviare rapidamente ed eseguire un progetto Data Quality per la pulizia dei dati utilizzando la Knowledge Base predefinita senza dover creare prima una nuova Knowledge Base in DQS.  
  
-   Eseguire le attività Gestione dominio, Individuazione informazioni o Criteri di corrispondenza sulla Knowledge Base predefinita. A tale scopo, fare clic su **Apri Knowledge Base** nel [schermata Data Quality Client Home](../data-quality-services/data-quality-client-home-screen.md), selezionare il **dati DQS** della knowledge base nel **Apri Knowledge Base** schermata e quindi selezionare l'attività richiesta nel **selezionare attività** area. Fare clic su **Avanti** per continuare.  
  
-   Creare una nuova Knowledge Base utilizzando una Knowledge Base predefinita. Per creare una knowledge base da una knowledge base esistente, vedere [creare una Knowledge Base](../data-quality-services/create-a-knowledge-base.md).  
  
-   Utilizzarla nel [componente pulizia DQS in Integration Services](http://go.microsoft.com/fwlink/?LinkId=238830) e [il componente aggiuntivo Master Data Services per Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## Vedere anche  
 [Knowledge Base e domini DQS](../data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  