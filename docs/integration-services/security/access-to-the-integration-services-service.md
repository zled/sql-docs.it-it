---
title: "Accesso al servizio Integration Services | Microsoft Docs"
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
  - "pacchetti SSIS, sicurezza"
  - "visualizzazione dei pacchetti in esecuzione"
  - "visualizzazione dei pacchetti in esecuzione"
  - "sicurezza [Integration Services], esecuzione di pacchetti"
  - "pacchetti [Integration Services], sicurezza"
  - "pacchetti correnti in esecuzione"
  - "pacchetti di Integration Services, sicurezza"
  - "pacchetti di SQL Server Integration Services, sicurezza"
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Accesso al servizio Integration Services
  Tramite i livelli di protezione dei pacchetti è possibile limitare gli utenti a cui è consentito modificare ed eseguire un pacchetto. Per limitare gli utenti a cui è consentito visualizzare l'elenco di pacchetti attualmente in esecuzione in un server e arrestare i pacchetti attualmente in esecuzione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è necessaria una protezione aggiuntiva.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] usa il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per visualizzare l'elenco dei pacchetti in esecuzione. I membri del gruppo Administrators di Windows possono visualizzare e arrestare tutti i pacchetti in esecuzione. Gli utenti che non appartengono a questo gruppo possono visualizzare e arrestare solo i pacchetti che hanno avviato personalmente.  
  
 È importante limitare l'accesso ai computer che eseguono un servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], soprattutto se si tratta di un servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che consente l'enumerazione di cartelle remote. Gli utenti autenticati possono richiedere l'enumerazione di pacchetti. Anche se il servizio non viene individuato, le cartelle vengono comunque enumerate dal servizio stesso. Questi nomi di cartella potrebbero essere sfruttati da un utente malintenzionato. Se un amministratore ha configurato il servizio in modo da consentire l'enumerazione di cartelle in un computer remoto, agli utenti potrebbero essere visualizzati anche i nomi di cartella in genere non visibili.  
  
  