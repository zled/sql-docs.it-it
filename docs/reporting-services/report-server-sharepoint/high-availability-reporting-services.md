---
title: "Disponibilit&#224; elevata (Reporting Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "disponibilità elevata [SQL Server], Reporting Services"
  - "disponibilità elevata [Reporting Services]"
  - "Reporting Services, disponibilità elevata"
ms.assetid: 50e0813f-f591-4688-9cd1-e6389a3808e5
caps.latest.revision: 16
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 16
---
# Disponibilit&#224; elevata (Reporting Services)
  Un server di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è un server senza stato (stateless) in cui vengono archiviati dati dell'applicazione, contenuto, proprietà e informazioni sulla sessione in due database relazionali di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In questa situazione, il modo più efficiente per garantire la disponibilità delle funzionalità di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] consiste nell'esecuzione delle operazioni seguenti:  
  
-   Utilizzare le caratteristiche a disponibilità elevata del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] per ottimizzare il tempo di attività dei database del server di report. Se si configura un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] per l'esecuzione in un cluster di failover, è possibile selezionarla quando si crea un database del server di report.  
  
-   Utilizzare, per quanto possibile, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] con i database di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e per le origini dati. Per altre informazioni, vedere [Reporting Services con i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/reporting-services-with-always-on-availability-groups-sql-server.md).  
  
-   Configurare più server di report in modo che vengano eseguiti in una distribuzione con scalabilità orizzontale, in cui tutti i server condividono un unico database del server di report. La distribuzione di più istanze del server di report, preferibilmente in server diversi, con scalabilità orizzontale consente di non interrompere il servizio ininterrotto nel caso in cui una delle istanze del server di report si arresti..  
  
 Una distribuzione con scalabilità orizzontale consente di condividere un database. Se uno server di report si arresta, gli altri server nella stessa distribuzione continueranno a funzionare.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non riesce a interagire con i cluster. Di per sé, una distribuzione con scalabilità orizzontale non fornisce il bilanciamento carico e non rileva i carichi di elaborazione su un server di report né invia le nuove richieste di elaborazione al server meno occupato. Tale distribuzione inoltre non reindirizza le richieste di elaborazione che non state completate in modo corretto. Per ottenere il bilanciamento del carico, è necessario configurarlo per i server Web che ospitano i server di report e configurare quindi i server di report in una distribuzione con scalabilità orizzontale in modo che condividano lo stesso database del server di report.  
  
 Il servizio Web ReportServer e il servizio Windows sono strettamente integrati e vengono eseguiti insieme come una sola istanza del server di report. Non è possibile configurare separatamente la disponibilità per uno dei due servizi.  
  
## Vedere anche  
 [Soluzioni a disponibilità elevata &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Configurare una distribuzione con scalabilità orizzontale di un server di report in modalità nativa &#40;Gestione configurazione&#41;](../Topic/Scale-out%20Deployment%20%20-%20Reporting%20Services%20Native%20mode%20\(Configuration%20Manager\).md)  
  
  