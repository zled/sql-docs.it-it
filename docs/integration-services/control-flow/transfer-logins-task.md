---
title: "Attivit&#224; Trasferisci account di accesso | Microsoft Docs"
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
  - "sql13.dts.designer.transferloginstask.f1"
helpviewer_keywords: 
  - "Trasferisci account di accesso - attività [Integration Services]"
ms.assetid: 1df60fd6-c019-405d-8155-c330dbac2cc1
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# Attivit&#224; Trasferisci account di accesso
  L'attività Trasferisci account di accesso trasferisce uno o più account di accesso tra istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Trasferimento di account di accesso tra istanze di SQL Server  
 L'attività Trasferisci account di accesso supporta un'origine e una destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Eventi  
 L'attività Trasferisci account di accesso genera un evento informativo in cui è indicato il numero di account di accesso trasferiti. Genera inoltre un evento di avviso quando un account di accesso viene sovrascritto.  
  
 Non viene riportato lo stato incrementale del trasferimento, ma solo il completamento 0% e 100%.  
  
## Valore di esecuzione  
 Il valore di esecuzione, definito nella proprietà **ExecutionValue** dell'attività, restituisce il numero di account di accesso trasferiti. Tramite l'assegnazione di una variabile definita dall'utente alla proprietà **ExecValueVariable** dell'attività, le informazioni sul trasferimento degli account di accesso possono essere rese disponibili ad altri oggetti del pacchetto. Per altre informazioni, vedere [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) e [Utilizzo di variabili nei pacchetti](../Topic/Use%20Variables%20in%20Packages.md).  
  
## Voci di log  
 L'attività Trasferisci account di accesso include le voci di log personalizzate seguenti:  
  
-   TransferLoginsTaskStarTransferringObjects    Indica che il trasferimento è iniziato. La voce di log include l'ora di inizio.  
  
-   TransferLoginsTaskFinishedTransferringObjects   Indica che il trasferimento è stato completato. La voce di log include l'ora di fine.  
  
 Inoltre, una voce di log per l'evento **OnInformation** indica il numero di account di accesso che sono stati trasferiti. Viene scritta una voce di log per l'evento **OnWarning** per ogni account di accesso sovrascritto nella destinazione.  
  
## Sicurezza e autorizzazioni  
 Per poter esplorare gli account di accesso nel server di origine e creare account di accesso nel server di destinazione, è necessario che l'utente sia un membro del ruolo del server sysadmin in entrambi i server.  
  
## Configurazione dell'attività Trasferisci account di accesso  
 È possibile configurare l'attività per il trasferimento di tutti gli account di accesso, degli account di accesso specificati o di tutti gli account di accesso che accedono ai database specificati. L'account di accesso sa non può essere trasferito. È possibile rinominare l'account di accesso sa. Dopo essere stato rinominato, tuttavia, l'account di accesso sa non può essere trasferito.  
  
 È inoltre possibile specificare se l'attività deve copiare gli identificatori di sicurezza (SID) associati agli account di accesso. Se l'attività Trasferisci account di accesso viene utilizzata insieme all'attività Trasferisci database, i SID devono essere copiati nella destinazione. Se non si esegue questa operazione, gli account di accesso trasferiti non vengono riconosciuti dal database di destinazione.  
  
 Nella destinazione gli account di accesso trasferiti vengono disabilitati e vi vengono assegnate password casuali. Un membro del ruolo sysadmin nel server di destinazione deve modificare le password e attivare gli account di accesso in modo che possano essere utilizzati.  
  
 Gli account di accesso da trasferire potrebbero essere già presenti nella destinazione. È possibile configurare l'attività Trasferisci account di accesso per la gestione degli account di accesso duplicati nei modi seguenti:  
  
-   Gli account di accesso duplicati vengono sovrascritti.  
  
-   In presenza di account di accesso duplicati l'attività ha esito negativo.  
  
-   Gli account di accesso duplicati vengono ignorati.  
  
 In fase di esecuzione l'attività Trasferisci account di accesso si connette al server di origine e al server di destinazione utilizzando due gestioni di connessione SMO. Le due gestioni vengono configurate separatamente dall'attività Trasferisci account di accesso, che tuttavia vi fa riferimento. Le gestioni connessioni SMO specificano il server e la modalità di autenticazione da utilizzare per l'accesso al server. Per altre informazioni, vedere [Gestione connessione file](../../integration-services/connection-manager/smo-connection-manager.md).  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic su uno degli argomenti seguenti:  
  
-   [Editor attività Trasferisci account di accesso &#40;pagina Generale&#41;](../../integration-services/control-flow/transfer-logins-task-editor-general-page.md)  
  
-   [Editor attività Trasferisci account di accesso &#40;pagina Account di accesso&#41;](../../integration-services/control-flow/transfer-logins-task-editor-logins-page.md)  
  
-   [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
 Per altre informazioni sull'impostazione di queste proprietà in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## Configurazione a livello di codice dell'attività Trasferisci account di accesso  
 Per ulteriori informazioni sull'impostazione di queste proprietà a livello di codice, fare clic sull'argomento seguente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.TransferLoginsTask.TransferLoginsTask>  
  
  