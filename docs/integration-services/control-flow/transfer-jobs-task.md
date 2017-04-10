---
title: "Attivit&#224; Trasferisci processi | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transferjobstask.f1"
helpviewer_keywords: 
  - "Trasferisci processi - attività [Integration Services]"
ms.assetid: 1bf33885-9c5b-47e4-a549-f5920b66a1de
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Attivit&#224; Trasferisci processi
  L'attività Trasferisci processi trasferisce uno o più processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tra istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 È possibile configurare l'attività per il trasferimento di tutti i processi o dei processi specificati. È inoltre possibile indicare se i processi trasferiti devono essere attivati o meno nella destinazione.  
  
 I processi da trasferire potrebbero essere già presenti nella destinazione. È possibile configurare l'attività Trasferisci processi per la gestione dei processi duplicati nei modi seguenti:  
  
-   I processi duplicati vengono sovrascritti.  
  
-   In presenza di processi duplicati l'attività ha esito negativo.  
  
-   I processi duplicati vengono ignorati.  
  
 In fase di esecuzione l'attività Trasferisci processi si connette al server di origine e al server di destinazione utilizzando una o più gestioni connessioni SMO. Le gestioni connessioni SMO vengono configurate separatamente dall'attività Trasferisci processi, che tuttavia vi fa riferimento. Le gestioni connessioni SMO specificano il server e la modalità di autenticazione da adottare per l'accesso al server. Per altre informazioni, vedere [Gestione connessione SMO](../../integration-services/connection-manager/smo-connection-manager.md).  
  
## Trasferimento di processi tra istanze di SQL Server  
 L'attività Trasferisci processi supporta un'origine e una destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non esiste alcuna limitazione relativamente alla versione da utilizzare come origine o destinazione.  
  
## Eventi  
 L'attività Trasferisci processi genera un evento informativo in cui è indicato il numero di processi trasferiti. Genera inoltre un evento di avviso quando un processo viene sovrascritto. Non viene riportato lo stato incrementale del trasferimento, ma solo il completamento 0% e 100%.  
  
## Valore di esecuzione  
 Il valore di esecuzione, definito nella proprietà **ExecutionValue** dell'attività, restituisce il numero di processi trasferiti. Tramite l'assegnazione di una variabile definita dall'utente alla proprietà **ExecValueVariable** dell'attività, le informazioni sul trasferimento dei processi possono essere rese disponibili ad altri oggetti del pacchetto. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) e [Utilizzo di variabili nei pacchetti](../Topic/Use%20Variables%20in%20Packages.md).  
  
## Voci di log  
 L'attività Trasferisci processi include le voci di log personalizzate seguenti:  
  
-   TransferJobsTaskStarTransferringObjects   Indica che il trasferimento è iniziato. La voce di log include l'ora di inizio.  
  
-   TransferJobsTaskFinishedTransferringObjects    Indica che il trasferimento è stato completato. La voce di log include l'ora di fine.  
  
 Inoltre, una voce di log per l'evento **OnInformation** indica il numero di processi che sono stati trasferiti. Viene scritta una voce di log per l'evento **OnWarning** per ogni processo sovrascritto nella destinazione.  
  
## Sicurezza e autorizzazioni  
 Per poter trasferire processi, l'utente deve essere un membro del ruolo predefinito del server sysadmin o di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nel database msdb, sia nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di origine che in quella di destinazione.  
  
## Configurazione dell'attività Trasferisci processi  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], fare clic su uno degli argomenti seguenti:  
  
-   [Editor attività Trasferisci processi &#40;pagina Generale&#41;](../../integration-services/control-flow/transfer-jobs-task-editor-general-page.md)  
  
-   [Editor attività Trasferisci processi &#40;pagina Processi&#41;](../../integration-services/control-flow/transfer-jobs-task-editor-jobs-page.md)  
  
-   [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
 Per informazioni sull'impostazione di queste proprietà a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferJobsTask.TransferJobsTask>  
  
## Attività correlate  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Vedere anche  
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  