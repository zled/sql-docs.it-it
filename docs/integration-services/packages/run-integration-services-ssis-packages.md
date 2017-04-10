---
title: "Eseguire pacchetti di Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti di Integration Services, esecuzione"
  - "pacchetti SSIS, esecuzione"
  - "pacchetti [Integration Services], esecuzione"
  - "pacchetti di SQL Server Integration Services, esecuzione"
  - "esecuzione di pacchetti [Integration Services]"
  - "esecuzione di pacchetti [Integration Services]"
  - "Integration Services, (Vedere anche pacchetti di Integration Services)"
ms.assetid: c5fecc23-6f04-4fb2-9a29-01492ea41404
caps.latest.revision: 65
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 61
---
# Eseguire pacchetti di Integration Services (SSIS)
  Per eseguire un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , è possibile usare vari strumenti, a seconda della posizione in cui sono archiviati tali pacchetti. Gli strumenti sono descritti nella tabella seguente.  
  
 Per archiviare un pacchetto nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , è possibile utilizzare il modello di distribuzione del progetto per distribuire il progetto nel server. Per informazioni, vedere [Distribuire progetti nel server Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
 Per archiviare un pacchetto nell'archivio pacchetti SSIS, nel database msdb o nel file system, è possibile utilizzare il modello di distribuzione del pacchetto. Per altre informazioni, vedere [Distribuzione del pacchetto legacy &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md).  
  
|Strumento|Pacchetti archiviati nel server Integration Services|Pacchetti archiviati nell'archivio pacchetti SSIS o nel database msdb|Pacchetti archiviati nel file system, all'esterno del percorso che fa parte dell'archivio pacchetti SSIS|  
|----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|  
|**SQL Server Data Tools**|No|No<br /><br /> È tuttavia possibile aggiungere un pacchetto esistente a un progetto dall'archivio pacchetti di [!INCLUDE[ssIS](../../includes/ssis-md.md)] , in cui è incluso il database msdb. L'aggiunta di un pacchetto esistente al progetto comporta la creazione di una copia locale del pacchetto nel file system.|Sì|  
|**SQL Server Management Studio, quando si è connessi a un'istanza del motore di database in cui è ospitato il server Integration Services**<br /><br /> Per altre informazioni, vedere [Finestra di dialogo Esecuzione pacchetto](../../integration-services/packages/execute-package-dialog-box.md)|Sì|No<br /><br /> È tuttavia possibile importare un pacchetto nel server da questi percorsi.|No<br /><br /> È tuttavia possibile importare un pacchetto nel server dal file system.|
|**SQL Server Management Studio, quando si è connessi a un'istanza del motore di database in cui è ospitato il server Integration Services abilitato come master di scalabilità orizzontale**<br /><br /> Per altre informazioni, vedere [Eseguire pacchetti nel servizio di scalabilità orizzontale](../../integration-services/run-packages-in-integration-services-ssis-scale-out.md)|Sì|No|No|
|**SQL Server Management Studio, quando è connesso al servizio Integration Services che gestisce l'archivio pacchetti SSIS**|No|Sì|No<br /><br /> È tuttavia possibile importare un pacchetto nell'archivio pacchetti di [!INCLUDE[ssIS](../../includes/ssis-md.md)] dal file system.|  
|**dtexec**<br /><br /> Per altre informazioni, vedere [dtexec Utility](../../integration-services/packages/dtexec-utility.md).|Sì|Sì|Sì|  
|**dtexecui**<br /><br /> Per altre informazioni, vedere [Riferimento all’interfaccia utente dell’utilità di esecuzione pacchetti &#40;DtExecUI&#41;](../../integration-services/packages/execute-package-utility-dtexecui-ui-reference.md)|No|Sì|Sì|  
|**SQL Server Agent**<br /><br /> Per pianificare un pacchetto, è possibile utilizzare un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.<br /><br /> Per altre informazioni, vedere [Processi di SQL Server Agent per i pacchetti](../../integration-services/packages/sql-server-agent-jobs-for-packages.md).|Sì|Sì|Sì|  
|**Stored procedure predefinita**<br /><br /> Per altre informazioni, vedere [catalog.start_execution &#40;database SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)|Sì|No|No|  
|**API gestita, tramite tipi e membri dello spazio dei nomi** <xref:Microsoft.SqlServer.Management.IntegrationServices> |Sì|No|No|  
|**API gestita, tramite tipi e membri dello spazio dei nomi** <xref:Microsoft.SqlServer.Dts.Runtime> |Non attualmente|Sì|Sì|  
  
## <a name="execution-and-logging"></a>Esecuzione e registrazione  
 È possibile abilitare la registrazione per i pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], nonché acquisire informazioni di run-time in file di log. Per altre informazioni, vedere [registrazione di Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md).  
  
 Per monitorare i pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che vengono distribuiti ed eseguiti nel server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], utilizzare i report delle operazioni. I report sono disponibili in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [Report per il server Integration Services](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
## <a name="related-tasks"></a>Attività correlate  
  
-   [Pianificare un pacchetto tramite SQL Server Agent](../../integration-services/packages/schedule-a-package-by-using-sql-server-agent.md)  
  
-   [Eseguire un pacchetto in SQL Server Data Tools](../../integration-services/packages/run-a-package-in-sql-server-data-tools.md)  
  
-   [Eseguire un pacchetto sul server SSIS mediante SQL Server Management Studio](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità dtexec](../../integration-services/packages/dtexec-utility.md)   
[Avviare l'Importazione/Esportazione guidata SQL Server](../../integration-services/import-export-data/start-the-sql-server-import-and-export-wizard.md)
  
  