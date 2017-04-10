---
title: "Monitoraggio dei log degli errori | Microsoft Docs"
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
  - "log [SQL Server]"
  - "prestazioni di database [SQL Server], errori"
  - "log applicazioni di Windows [SQL Server]"
  - "monitoraggio delle prestazioni [SQL Server], errori"
  - "prestazioni server [SQL Server], errori"
  - "confronto tra output del log degli errori e output del registro applicazioni"
  - "errori [SQL Server Agent], log"
  - "ottimizzazione di database [SQL Server], errori"
  - "monitoraggio di database [SQL Server], errori"
  - "log degli errori di SQL Server"
  - "log [SQL Server], log degli errori di SQL Server"
  - "log degli errori [SQL Server]"
  - "log [SQL Server], log applicazioni di Windows"
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Monitoraggio dei log degli errori
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alcuni eventi di sistema e definiti dall'utente vengono registrati nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e nel registro applicazioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Sia nel registro errori che nel registro applicazioni viene applicato automaticamente un timestamp a tutti gli eventi registrati. Utilizzare le informazioni contenute nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la risoluzione di problemi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Il registro applicazioni di Windows offre un quadro generale degli eventi generati nel sistema operativo Windows, nonché degli eventi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Tramite il Visualizzatore eventi di Windows è possibile visualizzare il contenuto del registro applicazioni di Windows e filtrare le informazioni. È possibile, ad esempio, filtrare eventi informativi, di avviso, di errore, di controllo con esito positivo e di controllo con esito negativo.  
  
## Confronto tra l'output del registro errori e l'output del registro applicazioni  
 Per identificare la causa di eventuali problemi, è possibile utilizzare sia il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che il registro applicazioni di Windows. Ad esempio, durante il monitoraggio del log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbero venire visualizzati messaggi di errore privi di informazioni sulla causa dell'errore. Confrontando la data e l'ora degli eventi riportate nel registro errori e la data e l'ora riportate nel registro applicazioni è possibile circoscrivere le possibili cause. Nel Visualizzatore file di log di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è possibile integrare in un unico elenco il log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il log di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e il registro applicazioni di Windows. Ciò consente di capire più facilmente gli eventi del server e gli eventi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correlati. Per ulteriori informazioni, vedere l'argomento "Visualizzatore file di log" nella documentazione online di SQL Server.  
  
## Contenuto della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Visualizzazione del log degli errori di SQL Server](../../tools/configuration-manager/viewing-the-sql-server-error-log.md)|Contiene informazioni sul log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e descrive come visualizzarlo.|  
|[Visualizzazione del registro applicazioni di Windows](../../tools/configuration-manager/viewing-the-windows-application-log.md)|Contiene informazioni sul registro applicazioni di Windows e descrive come visualizzarlo.|  
  
  