---
title: "Attivit&#224; di Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "script [Integration Services], attività"
  - "file [Integration Services], opzioni di attività"
  - "attività di flusso di lavoro [Integration Services]"
  - "Integration Services, attività"
  - "aggiunta di attività relative ai pacchetti"
  - "attività [Integration Services], elencate"
  - "attività SSIS"
  - "SSIS, attività"
  - "flusso di controllo [Integration Services], attività"
  - "attività [Integration Services]"
  - "raggruppamento di attività"
  - "attività [Integration Services], informazioni sulle attività"
  - "attività di SQL Server Integration Services"
  - "attività di preparazione dei dati [Integration Services]"
  - "operazioni sulle directory [Integration Services]"
ms.assetid: 75c8901d-6966-4af3-abe5-10af6dd9313b
caps.latest.revision: 51
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 51
---
# Attivit&#224; di Integration Services
  Le attività sono elementi del flusso di controllo che definiscono le unità di lavoro eseguite nel flusso di controllo di un pacchetto. Un pacchetto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è costituito da una o più attività. Se il pacchetto contiene più attività, queste ultime sono connesse e ordinate in sequenza nel flusso di controllo tramite vincoli di precedenza.  
  
 È inoltre possibile creare attività personalizzate utilizzando un linguaggio di programmazione che supporta COM, ad esempio Visual Basic, oppure un linguaggio di programmazione .NET, ad esempio C#.  
  
 Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], lo strumento grafico disponibile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per operare sui pacchetti, offre un'area di progettazione per la creazione del flusso di controllo dei pacchetti, oltre a editor personalizzati per la configurazione delle attività. È inoltre possibile programmare il modello a oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] per creare pacchetti a livello di codice.  
  
## Tipi di attività  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include i tipi di attività seguenti.  
  
 Attività Flusso di dati  
 Questa attività esegue flussi di dati per estrarre dati, applicare trasformazioni a livello di colonna e caricare dati.  
  
 Attività di preparazione dei dati  
 Queste attività consentono di effettuare le seguenti operazioni: copiare file e directory, scaricare file e dati, eseguire metodi Web, applicare operazioni a documenti XML ed eseguire il profiling dei dati per la pulitura.  
  
 Attività di flusso di lavoro  
 Queste attività comunicano con altri processi per eseguire pacchetti, programmi o file batch, scambiare messaggi tra pacchetti, inviare messaggi di posta elettronica, leggere dati di Strumentazione gestione Windows (WMI) e monitorare eventi WMI.  
  
 Attività di SQL Server  
 Queste attività consentono di copiare, inserire, eliminare, modificare e accedere a dati e oggetti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Attività di scripting  
 Queste attività consentono di estendere le funzionalità dei pacchetti tramite script.  
  
 Attività di Analysis Services  
 Queste attività consentono di creare, modificare, eliminare ed elaborare oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Attività di manutenzione  
 Queste attività consentono di eseguire funzioni amministrative quali il backup e la compattazione dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la ricompilazione e la riorganizzazione degli indici e l'esecuzione dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 Attività personalizzate  
 È inoltre possibile creare attività personalizzate utilizzando un linguaggio di programmazione che supporta COM, ad esempio Visual Basic, oppure un linguaggio di programmazione .NET, ad esempio C#. Se si desidera accedere a un'attività personalizzata in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], è possibile creare e registrare un'interfaccia utente per l'attività. Per altre informazioni, vedere [Sviluppo di un'attività personalizzata](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md).  
  
## Configurazione di attività  
 Un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] può contenere una singola attività, ad esempio un'attività Esegui SQL che elimina record in una tabella di database durante l'esecuzione del pacchetto. I pacchetti, tuttavia, contengono molte attività, ognuna delle quali è impostata per essere eseguita nel contesto del flusso di controllo del pacchetto. Possono includere attività anche i gestori di eventi, ovvero flussi di lavoro eseguiti in risposta a eventi di run-time.  
  
 Per altre informazioni sull'aggiunta di un'attività a un pacchetto tramite la finestra di progettazione di [!INCLUDE[ssIS](../../includes/ssis-md.md)], vedere [Aggiunta o eliminazione di un'attività o un contenitore in un flusso di controllo](../../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md).  
  
 Per altre informazioni sull'aggiunta di un'attività a un pacchetto a livello di codice, vedere [Aggiunta di attività a livello di programmazione](../../integration-services/building-packages-programmatically/adding-tasks-programmatically.md).  
  
 Le attività possono essere configurate individualmente utilizzando le finestre di dialogo personalizzate per le singole attività disponibili in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] oppure la finestra Proprietà inclusa in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Un pacchetto può includere più attività dello stesso tipo, ad esempio sei attività Esegui SQL, ognuna delle quali può essere configurata in modo diverso. Per altre informazioni, vedere [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md).  
  
## Gruppi e connessioni attività  
 Se un'attività contiene più attività, queste ultime sono connesse e ordinate in sequenza nel flusso di controllo tramite vincoli di precedenza. Per altre informazioni, vedere [Vincoli di precedenza](../../integration-services/control-flow/precedence-constraints.md).  
  
 Le attività possono essere raggruppate ed eseguite come una singola unità di lavoro oppure ripetute in un ciclo. Per altre informazioni, vedere [Contenitore Ciclo Foreach](../../integration-services/control-flow/foreach-loop-container.md), [Contenitore Ciclo For](../../integration-services/control-flow/for-loop-container.md) e [Contenitore Sequenza](../../integration-services/control-flow/sequence-container.md).  
  
## Attività correlate  
 [Aggiunta o eliminazione di un'attività o un contenitore in un flusso di controllo](../../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
  