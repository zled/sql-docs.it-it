---
title: "servizio writer SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VDI [SQL Server]"
  - "ripristino [SQL Server], servizio writer SQL"
  - "backup [SQL Server], durante l'esecuzione di SQL Server"
  - "Servizio Copia Shadow del volume"
  - "backup di volumi durante l'esecuzione [SQL Server]"
  - "Virtual Backup Device Interface [SQL Server]"
  - "servizio writer SQL"
  - "servizi [SQL Server], writer SQL"
  - "writer MSDE"
  - "VSS"
ms.assetid: 0f299867-f499-4c2a-ad6f-b2ef1869381d
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# servizio writer SQL
  Il servizio writer SQL offre funzionalità aggiuntive per il backup e il ripristino di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite l'infrastruttura del Servizio Copia Shadow del volume.  
  
 Il servizio SQL Writer viene installato automaticamente. Il servizio deve essere in esecuzione quando l'applicazione del servizio Copia Shadow del volume (VSS) richiede un backup o un ripristino. Per configurare il servizio, utilizzare l'applet Servizi [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Il servizio writer SQL viene installato in tutti i sistemi operativi.  
  
## Scopo  
 Durante l'esecuzione, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] viene bloccato e dispone dell'accesso esclusivo ai file di dati. Quando il servizio writer SQL non è in esecuzione, i programmi di backup in esecuzione in Windows non dispongono di accesso ai file di dati e per creare backup è necessario utilizzare il backup di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Utilizzare il servizio writer SQL per consentire ai programmi di backup di Windows di copiare i file di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durante l'esecuzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Servizio Copia Shadow del volume  
 Il Servizio Copia Shadow del volume (VSS) è costituito da un set di API COM che implementa un'infrastruttura per consentire l'esecuzione di backup dei volumi mentre le applicazioni in un sistema continuano a scrivere nei volumi. Tale servizio offre un'interfaccia uniforme, che consente la coordinazione tra le applicazioni utente per l'aggiornamento di dati sul disco, ovvero i writer, e quelle per il backup delle applicazioni, ovvero i richiedenti.  
  
 Il Servizio Copia Shadow del volume acquisisce e copia immagini stabili per il backup nei sistemi in esecuzione, in particolare nei server, senza ridurre inutilmente le prestazioni e la stabilità dei servizi offerti. Per ulteriori informazioni, vedere la documentazione del Servizio Copia Shadow del volume.  
  
## Virtual Backup Device Interface (VDI)  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è disponibile un'API denominata Virtual Backup Device Interface (VDI) che consente ai fornitori di software indipendenti di integrare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nei propri prodotti, in modo da fornire supporto per operazioni di backup e di ripristino. Queste API sono state progettate per offrire affidabilità e prestazioni ottimali e per supportare la gamma completa di funzionalità di backup e di ripristino di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], incluse tutte le capacità di backup a caldo e di snapshot.  
  
## Autorizzazioni  
 Il servizio writer SQL deve essere eseguito utilizzando l'account di **sistema locale** . Per la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il servizio writer SQL usa l'account di accesso **NT Service\SQLWriter**. Con l'account di accesso **NT Service\SQLWriter** il processo del servizio writer SQL può essere eseguito con un livello di privilegi più basso in un account designato come **senza account di accesso**. In questo modo viene limitata la vulnerabilità. Se il servizio writer SQL viene disabilitato, qualsiasi utilità basata su snapshot VSS, ad esempio System Center Data Protection Manager, e alcuni altri prodotti di terze parti vengono interrotti o, nel peggiore dei casi, vi è il rischio di eseguire backup di database non coerenti. Se né [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il sistema in cui si effettua l'esecuzione, né il sistema host (in caso di macchina virtuale) necessitano di altri elementi oltre al backup di [!INCLUDE[tsql](../../includes/tsql-md.md)], il servizio writer SQL può essere disabilitato in modo sicuro e l'account di accesso può essere rimosso.  Si noti che il servizio writer SQL può essere richiamato da un backup a livello di sistema o di volume, se il backup è basato direttamente o meno su snapshot. Alcuni prodotti per il backup del sistema usano VSS per evitare il blocco causato da file aperti o bloccati. Il servizio writer SQL necessita di autorizzazioni elevate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] perché nel corso delle proprie attività deve bloccare brevemente tutte le operazioni di I/O per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Funzionalità  
 Il servizio writer SQL supporta:  
  
-   Backup e ripristino completo del database, inclusi i cataloghi full-text  
  
-   Backup e ripristino differenziale  
  
-   Ripristino con spostamento  
  
-   Ridenominazione del database  
  
-   Backup di sola copia  
  
-   Recupero automatico dello snapshot del database  
  
 Il servizio writer SQL non supporta:  
  
-   Backup del log  
  
-   Backup di file e filegroup  
  
-   Ripristino di pagine  
  
  