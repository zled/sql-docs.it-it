---
title: "Lezione 3: Aggiungere la registrazione tramite SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 64cd24cc-ba8e-4bd7-b10b-6b80d8b04af6
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Lezione 3: Aggiungere la registrazione tramite SSIS
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] include funzionalità di registrazione che consentono di risolvere i problemi e monitorare l'esecuzione dei pacchetti offrendo una traccia degli eventi generati dalle attività e dai contenitori. Le caratteristiche di registrazione sono flessibili ed è possibile attivarle a livello di pacchetto o a livello di singole attività o contenitori del pacchetto. È possibile selezionare gli eventi che si desidera registrare e creare più log per un singolo pacchetto.  
  
La registrazione è garantita da un provider di log. Ogni provider di log è in grado di scrivere le informazioni di registrazione in diversi formati e tipi di destinazione. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] rende disponibili i provider di log seguenti:  
  
-   File di testo  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]  
  
-   Registro eventi di Windows  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  
  
-   File XML  
  
In questa lezione verrà creata una copia del pacchetto sviluppato nella [Lezione 2: Aggiungere cicli tramite SSIS](../integration-services/lesson-2-adding-looping-with-ssis.md). Usando questo nuovo pacchetto, verranno aggiunte e configurate funzionalità di registrazione per monitorare eventi specifici durante l'esecuzione del pacchetto. Se non è stata completata nessuna delle lezioni precedenti, è possibile copiare il pacchetto della lezione 2 completato incluso nell'esercitazione.  
  
> [!IMPORTANT]  
> Per eseguire questa esercitazione, è necessario il database di esempio **AdventureWorksDW2012** . Per altre informazioni sull'installazione e sulla distribuzione di **AdventureWorksDW2012** vedere [Esempi di Reporting Services su CodePlex](http://go.microsoft.com/fwlink/p/?LinkID=526910)  
  
## Argomenti della lezione  
In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Copia del pacchetto della lezione 2](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
-   [Passaggio 2: Aggiunta e configurazione di funzionalità di registrazione](../integration-services/step-2-adding-and-configuring-logging.md)  
  
-   [Passaggio 3: Test del pacchetto creato nella lezione 3 dell'esercitazione](../integration-services/step-3-testing-the-lesson-3-tutorial-package.md)  
  
## Inizio della lezione  
[Passaggio 1: Copia del pacchetto della lezione 2](../integration-services/step-1-copying-the-lesson-2-package.md)  
  
  
  
