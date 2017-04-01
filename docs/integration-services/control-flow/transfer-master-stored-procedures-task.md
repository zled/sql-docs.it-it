---
title: "Attivit&#224; Trasferisci stored procedure master | Microsoft Docs"
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
  - "sql13.dts.designer.transfermasterspstask.f1"
helpviewer_keywords: 
  - "Trasferisci stored procedure master - attività [Integration Services]"
ms.assetid: 81702560-48a3-46d1-a469-e41304c7af8e
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Attivit&#224; Trasferisci stored procedure master
  L'attività Trasferisci stored procedure master trasferisce una o più stored procedure definite dall'utente tra i database **master** di istanze diverse di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per trasferire una stored procedure dal database **master**, è necessario che il proprietario stored della procedure sia un dbo.  
  
 È possibile configurare l'attività Trasferisci stored procedure master per il trasferimento di tutte le stored procedure o delle stored procedure specificate. Questa attività non esegue la copia delle stored procedure di sistema.  
  
 È possibile che le stored procedure master da trasferire siano già presenti nella destinazione. È tuttavia possibile configurare l'attività Trasferisci stored procedure master per la gestione di eventuali stored procedure esistenti nei modi seguenti:  
  
-   Le stored procedure esistenti vengono sovrascritte.  
  
-   In presenza di stored procedure duplicate l'attività ha esito positivo.  
  
-   Le stored procedure duplicate vengono ignorate.  
  
 In fase di esecuzione l'attività Trasferisci stored procedure master si connette al server di origine e al server di destinazione utilizzando due gestioni connessioni SMO. Le gestioni connessioni SMO vengono configurate separatamente dall'attività Trasferisci stored procedure master, che tuttavia vi fa riferimento. Le gestioni connessioni SMO specificano il server e la modalità di autenticazione da utilizzare per l'accesso al server. Per altre informazioni, vedere [Gestione connessione SMO](../../integration-services/connection-manager/smo-connection-manager.md).  
  
## Trasferimento di stored procedure tra istanze di SQL Server  
 L'attività Trasferisci stored procedure master supporta un'origine e una destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Eventi  
 L'attività genera un evento informativo in cui è indicato il numero di stored procedure trasferite. Genera inoltre un evento di avviso quando una stored procedure viene sovrascritta.  
  
 Non viene riportato lo stato incrementale del trasferimento, ma solo il completamento 0% e 100%.  
  
## Valore di esecuzione  
 Il valore di esecuzione, definito nella proprietà **ExecutionValue** dell'attività, restituisce il numero di stored procedure trasferite. Tramite l'assegnazione di una variabile definita dall'utente alla proprietà **ExecValueVariable** dell'attività, le informazioni sul trasferimento di stored procedure master possono essere rese disponibili ad altri oggetti del pacchetto. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) e [Utilizzo di variabili nei pacchetti](../Topic/Use%20Variables%20in%20Packages.md).  
  
## Voci di log  
 L'attività Trasferisci stored procedure master include le voci di log personalizzate seguenti:  
  
-   TransferStoredProceduresTaskStartTransferringObjects  Indica che il trasferimento è iniziato. La voce di log include l'ora di inizio.  
  
-   TransferSStoredProceduresTaskFinishedTransferringObjects  Indica che il trasferimento è stato completato. La voce di log include l'ora di fine.  
  
 Inoltre, una voce di log per l'evento **OnInformation** indica il numero di stored procedure che sono state trasferite e viene scritta una voce di log per l'evento **OnWarning** per ogni stored procedure sovrascritta nella destinazione.  
  
## Sicurezza e autorizzazioni  
 L'utente deve disporre dell'autorizzazione per la visualizzazione dell'elenco di stored procedure nel database **master** dell'origine ed essere un membro del ruolo del server amministratore di sistema o disporre dell'autorizzazione per la creazione di stored procedure nel database **master** del server di destinazione.  
  
## Configurazione dell'attività Trasferisci stored procedure master  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], fare clic su uno degli argomenti seguenti:  
  
-   [Editor attività Trasferisci stored procedure master &#40;pagina Generale&#41;](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-general-page.md)  
  
-   [Editor attività Trasferisci stored procedure master &#40;pagina Stored procedure&#41;](../../integration-services/control-flow/transfer-master-stored-procedures-task-editor-stored-procedures-page.md)  
  
-   [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
 Per informazioni sull'impostazione di queste proprietà a livello di codice, fare clic sull'argomento seguente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferStoredProceduresTask.TransferStoredProceduresTask>  
  
### Configurazione dell'attività Trasferisci stored procedure master a livello di codice  
  
## Attività correlate  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Vedere anche  
 [Attività Trasferisci oggetti di SQL Server](../../integration-services/control-flow/transfer-sql-server-objects-task.md)   
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  