---
title: "Attivit&#224; Invia messaggi | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sendmailtask.f1"
helpviewer_keywords: 
  - "posta elettronica [Integration Services]"
  - "Invia messaggi - attività"
  - "posta elettronica [Integration Services]"
  - "messaggi [Integration Services]"
  - "sending messages"
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
caps.latest.revision: 51
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 51
---
# Attivit&#224; Invia messaggi
  L'attività Invia messaggi consente di inviare un messaggio di posta elettronica. Tramite l'attività Invia messaggi un pacchetto può inviare messaggi quando le attività nel flusso di lavoro del pacchetto vengono completate o non riescono oppure in risposta a un evento generato dal pacchetto in fase di esecuzione. È ad esempio possibile utilizzare questa attività per notificare all'amministratore di un database l'esito positivo o negativo dell'attività Backup database.  
  
 Per configurare l'attività Invia messaggi, procedere nel modo seguente:  
  
-   Specificare il testo del messaggio di posta elettronica.  
  
-   Specificare l'oggetto del messaggio di posta elettronica.  
  
-   Impostare il livello di priorità del messaggio. L'attività supporta tre livelli di priorità: normale, medio e alto.  
  
-   Specificare i destinatari nelle righe A, Cc e Ccn. Per specificare più destinatari, separarli con punti e virgola.  
  
    > [!NOTE]  
    >  Le righe A, Cc e Ccn presentano il limite di 256 caratteri ognuna, in conformità agli standard Internet.  
  
-   Includere eventuali allegati. Per specificare più allegati, separarli con una barra verticale (|).  
  
    > [!NOTE]  
    >  Se un file allegato non esiste al momento dell'esecuzione del pacchetto, verrà generato un errore.  
  
-   Specificare la gestione connessione SMTP da utilizzare.  
  
    > [!IMPORTANT]  
    >  La gestione connessione SMTP supporta solo l'autenticazione anonima e l'autenticazione di Windows. Non supporta l'autenticazione di base.  
  
 Il testo del messaggio può essere una stringa specificata, una connessione a un file che contiene il testo o il nome di una variabile che contiene il testo. Per connettersi a un file l'attività utilizza una gestione connessione file. Per ulteriori informazioni, vedere [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
 Per connettersi a un server di posta elettronica l'attività utilizza una gestione connessione SMTP. Per altre informazioni, vedere [Gestione connessione SMTP](../../integration-services/connection-manager/smtp-connection-manager.md).  
  
## Messaggi di registrazione personalizzati disponibili nell'attività Invia messaggi  
 Nella tabella seguente sono elencate le voci di log personalizzate disponibili per l'attività Invia messaggi. Per altre informazioni, vedere [Registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md) e [Messaggi personalizzati per la registrazione](../../integration-services/performance/custom-messages-for-logging.md).  
  
|Voce di log|Description|  
|---------------|-----------------|  
|**SendMailTaskBegin**|Indica che l'attività ha iniziato a inviare un messaggio di posta elettronica.|  
|**SendMailTaskEnd**|Indica che l'attività ha terminato l'invio di un messaggio di posta elettronica.|  
|**SendMailTaskInfo**|Offre informazioni descrittive sull'attività.|  
  
## Configurazione dell'attività Invia messaggi  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], fare clic su uno degli argomenti seguenti:  
  
-   [Editor attività Invia messaggi &#40;pagina Generale&#41;](../../integration-services/control-flow/send-mail-task-editor-general-page.md)  
  
-   [Editor attività Invia messaggi &#40;pagina Messaggio&#41;](../../integration-services/control-flow/send-mail-task-editor-mail-page.md)  
  
-   [Pagina Espressioni](../../integration-services/expressions/expressions-page.md)  
  
 Per informazioni sull'impostazione di queste proprietà a livello di codice, fare clic sull'argomento seguente:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## Attività correlate  
 Per informazioni su come impostare queste proprietà nella finestra di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], fare clic su [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md).  
  
## Contenuto correlato  
  
-   Articolo tecnico relativo all'[invio della posta elettronica con notifica di recapito in C#](http://go.microsoft.com/fwlink/?LinkId=237625) su shareourideas.com  
  
## Vedere anche  
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  