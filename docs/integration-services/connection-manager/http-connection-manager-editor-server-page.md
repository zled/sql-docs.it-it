---
title: "Editor gestione connessione HTTP (pagina Server) | Microsoft Docs"
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
  - "sql13.dts.designer.httpconnection.server.f1"
helpviewer_keywords: 
  - "Editor gestione connessione HTTP"
ms.assetid: 774778a0-ece6-4971-b93f-b121d8fc1fc1
caps.latest.revision: 32
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 32
---
# Editor gestione connessione HTTP (pagina Server)
  La scheda **Server** della finestra di dialogo **Editor gestione connessione HTTP** consente di configurare la gestione connessione HTTP specificando proprietà quali l'URL e le credenziali di sicurezza. Una connessione HTTP consente a un pacchetto di accedere al server Web utilizzando il protocollo HTTP per l'invio o la ricezione di file. Dopo aver configurato la gestione connessione HTTP sarà inoltre possibile verificare la connessione.  
  
> [!IMPORTANT]  
>  La gestione connessione HTTP supporta solo l'autenticazione anonima e l'autenticazione di base. Non supporta l'autenticazione di Windows.  
  
 Per ulteriori informazioni sulla gestione connessione HTTP, vedere [HTTP Connection Manager](../../integration-services/connection-manager/http-connection-manager.md). Per ulteriori informazioni su uno scenario di utilizzo comune della gestione connessione HTTP, vedere [Web Service Task](../../integration-services/control-flow/web-service-task.md).  
  
## Opzioni  
 **URL server**  
 Digitare l'URL per il server.  
  
 Se si intende utilizzare il pulsante **Scarica WSDL** nella pagina **Generale** di **Editor attività Servizio Web** per scaricare un file WSDL, digitare l'URL del file WSDL. L'URL termina con "?wsdl".  
  
 **Usa credenziali**  
 Consente di specificare se si desidera che per la gestione connessione HTTP vengano utilizzate le credenziali di sicurezza dell'utente per l'autenticazione.  
  
 **Nome utente**  
 Se per la gestione connessione HTTP è stato impostato l'utilizzo di credenziali, è necessario specificare nome utente, password e dominio.  
  
 **Password**  
 Se per la gestione connessione HTTP è stato impostato l'utilizzo di credenziali, è necessario specificare nome utente, password e dominio.  
  
 **Dominio**  
 Se per la gestione connessione HTTP è stato impostato l'utilizzo di credenziali, è necessario specificare nome utente, password e dominio.  
  
 **Usa certificato client**  
 Consente di specificare se si desidera che per la gestione connessione HTTP venga utilizzato un certificato client per l'autenticazione.  
  
 **Certificato**  
 Consente di selezionare un certificato nell'elenco usando la finestra di dialogo **Seleziona certificato**. Nella casella di testo viene visualizzato il nome associato al certificato.  
  
 **Timeout (in secondi)**  
 Consente di fornire un valore di timeout per la connessione al server Web. Il valore predefinito di questa proprietà è 30 secondi.  
  
 **Dimensioni blocco (in KB)**  
 Consente di specificare le dimensioni del blocco per la scrittura dei dati.  
  
 **Test connessione**  
 Dopo aver configurato la gestione connessione HTTP, fare clic su **Test connessione** per assicurarsi che la connessione sia operativa.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor gestione connessione HTTP &#40;pagina Proxy&#41;](../../integration-services/connection-manager/http-connection-manager-editor-proxy-page.md)  
  
  