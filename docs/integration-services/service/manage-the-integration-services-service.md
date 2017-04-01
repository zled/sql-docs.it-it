---
title: "Gestione del servizio Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizio Integration Services, configurazione"
  - "servizi [Integration Services], configurazione"
ms.assetid: 45554117-a0df-4830-b41c-5ebb33b764a5
caps.latest.revision: 63
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 63
---
# Gestione del servizio Integration Services
    
> **IMPORTANTE** In questo argomento viene illustrato il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , un servizio Windows per la gestione dei pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] supporta il servizio per la compatibilità con le versioni precedenti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], è possibile gestire oggetti come i pacchetti del server Integration Services.  
  
 Quando viene installato il componente [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], viene installato anche il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene avviato e impostato per l'avvio automatico. È tuttavia necessario installare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per utilizzare il servizio per la gestione di pacchetti [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] archiviati e in esecuzione.  
  
> **NOTA:** per connettersi direttamente a un'istanza del servizio Integration Services legacy, è necessario usare la versione di SQL Server Management Studio (SSMS) allineata alla versione di SQL Server in cui è in esecuzione il servizio Integration Services. Ad esempio, per connettersi al servizio Integration Services legacy in esecuzione in un'istanza di SQL Server 2016, è necessario usare la versione di SQL Server Management Studio rilasciata per SQL Server 2016. [Scaricare SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
>
>   Nella finestra di dialogo **Connetti al server** di SQL Server Management Studio non è possibile specificare il nome di un server sul quale è in esecuzione una versione precedente del servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Per gestire i pacchetti archiviati in un server remoto, tuttavia, non è necessario connettersi all'istanza del servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel server remoto in questione. Modificare, invece, il file di configurazione per il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in modo che in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] vengano visualizzati i pacchetti archiviati nel server remoto. Per altre informazioni, vedere [Configurazione del servizio Integration Services &#40;SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
 È possibile installare solo una singola istanza del servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in un computer. Il servizio non è specifico di una particolare istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Connettersi al servizio utilizzando il nome del computer sul quale è in esecuzione il servizio.  
  
 Per la gestione del servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è possibile usare uno dei seguenti snap-in di Microsoft Management Console (MMC): Gestione configurazione SQL Server o Servizi di SQL Server. Per gestire pacchetti in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], è prima di tutti necessario assicurarsi che il servizio sia avviato.  
  
 Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è configurato per gestire i pacchetti archiviati nel database msdb dell'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] installata in contemporanea con [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Se contemporaneamente non viene installata alcuna istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)], il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è configurato per gestire i pacchetti contenuti nel database msdb dell'istanza predefinita locale del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Per gestire pacchetti archiviati in un'istanza denominata o un'istanza remota del [!INCLUDE[ssDE](../../includes/ssde-md.md)] o in più istanze del [!INCLUDE[ssDE](../../includes/ssde-md.md)], è necessario modificare il file di configurazione per il servizio. Per altre informazioni, vedere [Configurazione del servizio Integration Services &#40;SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md).  
  
 Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è configurato in modo che i pacchetti in esecuzione vengano arrestati all'arresto del servizio. Il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], tuttavia, non attende che i pacchetti vengano arrestati e l'esecuzione di alcuni pacchetti potrebbe continuare dopo l'arresto del servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Se il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene arrestato, è possibile continuare a eseguire pacchetti tramite l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], l'Utilità di esecuzione pacchetti e l'utilità del prompt dei comandi **dtexec** (dtexec.exe). Non è tuttavia possibile eseguire il monitoraggio dei pacchetti in esecuzione.  
  
 Per impostazione predefinita, il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene eseguito nel contesto dell'account NETWORK SERVICE.  
  
 Il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] esegue registrazioni nel registro eventi di Windows. È possibile visualizzare gli eventi del servizio in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. È anche possibile visualizzare gli eventi del servizio utilizzando il Visualizzatore eventi di Windows.  
  
### Per impostare le proprietà del servizio Integration Services tramite lo snap-in Servizi  
  
-   [Impostare le proprietà del servizio Integration Services](../../integration-services/service/set-the-properties-of-the-integration-services-service.md)  
  
### Per visualizzare gli eventi per il servizio di Integration Services  
  
-   [Visualizzare eventi per il servizio Integration Services](../../integration-services/service/view-events-for-the-integration-services-service.md)  
  
## Vedere anche  
 [Servizio Integration Services &#40;servizio SSIS&#41;](../../integration-services/service/integration-services-service-ssis-service.md)   
 [Configurazione del servizio Integration Services &#40;servizio SSIS&#41;](../../integration-services/service/configuring-the-integration-services-service-ssis-service.md)   
 [Importazione/Esportazione guidata SQL Server](../Topic/SQL%20Server%20Import%20and%20Export%20Wizard.md)   
 [Utilità dtexec](../../integration-services/packages/dtexec-utility.md)   
 [Esecuzione di progetti e pacchetti](https://msdn.microsoft.com/library/ms141708(v=sql.130).aspx)  
  
  