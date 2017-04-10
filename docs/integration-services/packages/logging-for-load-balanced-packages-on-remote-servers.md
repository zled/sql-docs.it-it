---
title: "Registrazione per pacchetti con bilanciamento del carico in server remoti | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "log [Integration Services], pacchetti remoti"
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# Registrazione per pacchetti con bilanciamento del carico in server remoti
  La gestione dei log di tutti i pacchetti figlio in esecuzione su più server risulta più semplice se tutti i pacchetti figlio utilizzano lo stesso provider di log e scrivono nella stessa destinazione. Per creare un file di log comune per tutti i pacchetti figlio, è possibile configurare i pacchetti figlio in modo da registrare i propri eventi in un provider di log di tipo SQL Server. È possibile configurare tutti i pacchetti in modo che utilizzino lo stesso database, lo stesso server e la stessa istanza del server.  
  
 Per visualizzare tutti i file di log, l'amministratore deve semplicemente accedere a un server e visualizzare il file di log per tutti i pacchetti figlio.  
  
## Attività correlate  
 Per informazioni su come abilitare la registrazione in un pacchetto, vedere [Abilitare la registrazione di pacchetti in SQL Server Data Tools](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md).  
  
## Vedere anche  
 [Registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md)  
  
  