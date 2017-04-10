---
title: "Servizio Integration Services (servizio SSIS) | Microsoft Docs"
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
  - "servizio Integration Services, informazioni sul servizio Integration Services"
  - "SQL Server Integration Services - servizio"
  - "servizio [Integration Services], informazioni sul servizio Integration Services"
  - "servizio [Integration Services]"
  - "SQL Server Integration Services, servizio"
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
caps.latest.revision: 61
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 61
---
# Servizio Integration Services (servizio SSIS)
  Negli argomenti contenuti in questa sezione viene illustrato il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], un servizio Windows per la gestione dei pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Questo servizio non è necessario per creare, salvare ed eseguire i pacchetti di Integration Services. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] supporta il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]per la compatibilità con le versioni precedenti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] archivia oggetti, impostazioni e dati operativi nel database **SSISDB** per i progetti distribuiti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] usando il modello di distribuzione del progetto. Nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], che è un'istanza del motore di database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è ospitato il database. Per altre informazioni sul database, vedere [Catalogo SSIS](../../integration-services/service/ssis-catalog.md). Per altre informazioni sulla distribuzione di progetti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vedere [Distribuire progetti nel server Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
## Funzionalità di gestione  
 Il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è un servizio Windows per la gestione di pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è disponibile solo in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] consente di eseguire le attività di gestione seguenti:  
  
-   Avvio di pacchetti locali o archiviati in una posizione remota  
  
-   Arresto di pacchetti eseguiti localmente o in modalità remota  
  
-   Monitoraggio di pacchetti eseguiti localmente o in modalità remota  
  
-   Importazione ed esportazione di pacchetti  
  
-   Gestione dell'archiviazione di pacchetti  
  
-   Personalizzazione delle cartelle di archiviazione  
  
-   Arresto dei pacchetti in esecuzione quando il servizio viene arrestato  
  
-   Visualizzazione del registro eventi di Windows  
  
-   Connessione a più server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
## Tipo di avvio per il servizio Integration Services  
 Il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene installato quando si installa il componente [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene avviato in base al tipo di avvio automatico. È necessario che sia in esecuzione se si desidera eseguire il monitoraggio dei pacchetti archiviati nell'archivio pacchetti [!INCLUDE[ssIS](../../includes/ssis-md.md)]. L'archivio pacchetti [!INCLUDE[ssIS](../../includes/ssis-md.md)] può essere il database msdb di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o le cartelle designate del file system.  
  
 Il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] non è necessario se si desidera semplicemente progettare ed eseguire pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. È invece necessario per elencare e monitorare i pacchetti tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## Attività correlate  
  
-   [Impostare le proprietà del servizio Integration Services](../../integration-services/service/set-the-properties-of-the-integration-services-service.md)  
  
-   [Visualizzare eventi per il servizio Integration Services](../../integration-services/service/view-events-for-the-integration-services-service.md)  
  
  