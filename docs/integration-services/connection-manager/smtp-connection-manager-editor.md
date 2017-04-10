---
title: "Editor gestione connessione SMTP | Microsoft Docs"
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
  - "sql13.dts.designer.smtpconnection.f1"
helpviewer_keywords: 
  - "Editor gestione connessione SMTP"
ms.assetid: 2693de0d-b04d-4325-a856-ce667d2b8aa1
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# Editor gestione connessione SMTP
  Usare la finestra di dialogo **Editor gestione connessioni SMTP** per specificare un server SMTP (Simple Mail Transfer Protocol).  
  
 Per ulteriori informazioni sulla gestione connessioni SMTP, vedere [SMTP Connection Manager](../../integration-services/connection-manager/smtp-connection-manager.md).  
  
## Opzioni  
 **Nome**  
 Consente di specificare un nome univoco per la gestione connessione.  
  
 **Description**  
 Consente di aggiungere una descrizione per la gestione connessione. È consigliabile includere nella descrizione informazioni sugli scopi della gestione connessione, in modo da ottenere pacchetti autodocumentati e semplificarne quindi la gestione.  
  
 **Server SMTP**  
 Consente di specificare il nome del server SMTP.  
  
 **Usa autenticazione di Windows**  
 Selezionare questa opzione per inviare la posta elettronica mediante un server SMTM che utilizza l'autenticazione di Windows per consentire l'accesso.  
  
> [!IMPORTANT]  
>  La gestione connessione SMTP supporta solo l'autenticazione anonima e l'autenticazione di Windows. Non supporta l'autenticazione di base.  
  
> [!NOTE]  
>  Se si utilizza Microsoft Exchange come server SMTP, potrebbe essere necessario impostare l'opzione **Usa autenticazione di Windows** su **True**. È possibile configurare i server Exchange in modo da impedire le connessioni SMTP non autenticate.  
  
 **Attiva SSL (Secure Sockets Layer)**  
 Selezionare questa opzione per crittografare le comunicazioni mediante SSL (Secure Sockets Layer) durante l'invio di messaggi di posta elettronica.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
  
  