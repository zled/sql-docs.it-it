---
title: "Editor gestione connessione FTP | Microsoft Docs"
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
  - "sql13.dts.designer.ftpconnectionmanager.f1"
helpviewer_keywords: 
  - "Editor gestione connessione FTP"
ms.assetid: 874b6585-255b-4a43-8396-bb08c3e8ac2b
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Editor gestione connessione FTP
  Usare la finestra di dialogo **Editor gestione connessione FTP** per specificare le proprietà per la connessione a un server FTP.  
  
> [!IMPORTANT]  
>  La gestione connessione FTP supporta solo l'autenticazione anonima e l'autenticazione di base. Non supporta l'autenticazione di Windows.  
  
 Per altre informazioni sulla gestione connessione FTP, vedere [Gestione connessione FTP](../../integration-services/connection-manager/ftp-connection-manager.md).  
  
## Opzioni  
 **Nome server**  
 Consente di specificare il nome del server FTP.  
  
 **Porta server**  
 Consente di specificare il numero di porta del server FTP da utilizzare per la connessione. Il valore predefinito di questa proprietà è **21**.  
  
 **Nome utente**  
 Consente di specificare un nome utente per l'accesso al server FTP. Il valore predefinito di questa proprietà è **anonymous**.  
  
 **Password**  
 Consente di specificare una password per l'accesso al server FTP.  
  
 **Timeout (in secondi)**  
 Consente di specificare il numeri di secondi di attesa prima che si verifichi il timeout dell'attività. Il valore **0** indica un periodo di tempo infinito. Il valore predefinito di questa proprietà è **60**.  
  
 **Usa modalità passiva**  
 Consente di specificare se la connessione viene iniziata dal server o dal client. Il server inizia la connessione in modalità attiva, mentre il client attiva la connessione in modalità passiva. Il valore predefinito di questa proprietà è **active mode**.  
  
 **Tentativi**  
 Consente di specificare il numeri di tentativi eseguiti dall'attività per stabilire la connessione. Il valore **0** indica un numero di tentativi illimitato.  
  
 **Dimensioni blocco (in KB)**  
 Consente di specificare le dimensioni del blocco in KB per la trasmissione dei dati.  
  
 **Test connessione**  
 Dopo aver configurato la gestione connessione FTP, fare clic su **Test connessione** per assicurarsi che la connessione sia funzionante.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
  
  