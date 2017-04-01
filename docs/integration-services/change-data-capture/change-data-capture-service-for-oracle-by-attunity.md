---
title: "Servizio Change Data Capture per Oracle di Attunity | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# Servizio Change Data Capture per Oracle di Attunity
  Il servizio CDC per Oracle è un servizio Windows tramite cui vengono analizzati i log delle transazioni Oracle e acquisite le modifiche apportate alle tabelle Oracle di interesse nelle tabelle delle modifiche di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Le tabelle delle modifiche SQL in cui vengono archiviate le modifiche acquisite da Oracle sono dello stesso tipo delle tabelle delle modifiche usate nella funzionalità Change Data Capture nativa di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In questo modo l'utilizzo delle modifiche è facile quanto l'utilizzo delle modifiche apportate ai database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## Installation  
 Microsoft® Change Data Capture Designer and Service per Oracle di Attunity per Microsoft SQL Server® 2016 fanno parte del Feature Pack di SQL Server 2016. I componenti del Feature Pack sono disponibili per il download nella [pagina Web del Feature Pack di SQL Server 2016](http://go.microsoft.com/fwlink/?LinkId=746297).  
  
 È possibile installare il servizio CDC per Oracle in qualsiasi computer Windows supportato con accesso al o ai database Oracle di origine che vengono acquisiti e all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione in cui si trova il database CDC di destinazione. Per il servizio CDC non è necessaria un'installazione locale del database Oracle o del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ma solo dei relativi client supportati. Per altre informazioni sul percorso di installazione dei componenti di database richiesti, vedere **Prerequisiti del database** in questo argomento.  
  
 Con l'installazione del servizio CDC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per Oracle l'interfaccia utente della configurazione del servizio e il programma del servizio vengono posizionati nel percorso selezionato. Il servizio CDC per Oracle viene configurato separatamente tramite Oracle CDC Service Configuration Console. Per altre informazioni sulla configurazione del servizio Oracle CDC, vedere [Change Data Capture Service for Oracle by Attunity F1 Help](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md).  
  
 È possibile installare il servizio CDC per Oracle in qualsiasi computer Windows supportato in cui sia installato il client nativo di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ; non è necessario che sia installato nello stesso computer in cui si trova l'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione.  
  
## Ambienti Windows supportati  
 È possibile eseguire il servizio Change Data Capture per Oracle di Attunity negli ambienti Windows seguenti:  
  
-   Windows Vista con Service Pack 2  
  
-   Windows 7  
  
-   Windows 8 e 8.1  
  
-   Windows 10  
  
-   Windows Server 2008 R2  
  
-   Windows Server 2008 con Service Pack 2  
  
-   Windows Server 2012  
  
## Prerequisiti del database  
 Per usare il servizio CDC per Oracle, è necessario installare il software Oracle [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client. Si tratta di un prerequisito che è necessario ottenere da Oracle e installare prima dell'installazione del servizio Oracle CDC. Inoltre, è necessario installare il client ODBC di SQL Server usando il programma di installazione di SQL Server.  
  
 Il servizio CDC per Oracle supporta le versioni seguenti:  
  
### Database Oracle di origine  
  
-   Oracle Database 11x, qualsiasi versione  
  
-   Oracle Database 10x, qualsiasi versione  
  
-   Database Oracle 10g Release 2: 10.2.0.1-10.2.0.5 (set di patch a partire da aprile 2010)  
  
-   Database Oracle 11g Release 1: 11.1.0.6-11.1.0.7 (set di patch a partire da settembre 2008)  
  
-   Database Oracle 11g Release 2: 11.2.0.1-11.2.0.3 (set di patch a partire da settembre 2011)  

-   Oracle Database 12c nell'installazione classica. L'installazione multi-tenant non è supportata.  
  
### Database di SQL Server di destinazione  
 Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
## Esecuzione del programma di installazione  
 Per installare il servizio CDC per Oracle, aprire l'Installazione guidata per la piattaforma Windows in uso (32/64 bit) e attenersi alle indicazioni visualizzate sullo schermo.  
  
## Disinstallazione del servizio Change Data Capture per Oracle di Attunity  
 Per disinstallare il servizio CDC per Oracle, scegliere Pannello di controllo, Programmi e funzionalità.  
  
 Con la disinstallazione del servizio CDC, non vengono eliminati i database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creati. Per la rimozione completa dello strumento, è necessario rimuovere il database MSXDBCDC e i database CDC specifici creati nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione usata.  
  
 Se si disinstalla il software del servizio CDC da un computer e lo si installa in un altro computer, è sufficiente fornire le definizioni seguenti:  
  
-   Account servizio  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - Stringa di connessione e credenziali  
  
-   Master password  
  
 Tutte le altre definizioni vengono archiviate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e sono disponibile dall'installazione precedente in un altro computer.  
  
## Contenuto della documentazione  
  
-   [Architettura di sistema del servizio Change Data Capture per Oracle di Attunity](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [Servizio Oracle CDC](../../integration-services/change-data-capture/the-oracle-cdc-service.md)  
  
-   [Guida del servizio Change Data Capture per Oracle di Attunity](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [Guida procedurale del servizio Change Data Capture per Oracle di Attunity](../../integration-services/change-data-capture/change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## Vedere anche  
 [Utilizzo del servizio Oracle CDC](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md)  
  
  