---
title: "Progetti e soluzioni di Integration Services (SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.importprojectwizard.f1"
helpviewer_keywords: 
  - "progetti [Integration Services], creazione"
  - "cartelle [Integration Services], progetti"
  - "file [Integration Services], progetti"
  - "cartelle [Integration Services]"
  - "progetti [Integration Services], informazioni sui progetti"
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
caps.latest.revision: 63
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 62
---
# Progetti e soluzioni di Integration Services (SSIS)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fornisce [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per lo sviluppo di pacchetti [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 Quando si distribuiscono i pacchetti in un database [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] o nell'archivio pacchetti [!INCLUDE[ssIS](../includes/ssis-md.md)], usare il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] per gestire i pacchetti. Il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] è disponibile solo in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Per altre informazioni sul servizio, vedere [Servizio Integration Services &#40;servizio SSIS&#41;](../integration-services/service/integration-services-service-ssis-service.md). Per altre informazioni sulla distribuzione dei pacchetti, vedere [Distribuzione del pacchetto legacy &#40;SSIS&#41;](../integration-services/packages/legacy-package-deployment-ssis.md).  
  
 Quando si distribuiscono progetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] nel server [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], per gestire i progetti si utilizzano le viste e le stored procedure Transact-SQL in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Per altre informazioni sulla distribuzione dei progetti, vedere [Distribuzione di progetti e pacchetti](https://msdn.microsoft.com/library/hh213290.aspx). Per altre informazioni sul server [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vedere [Integration Services &#40;SSIS&#41; Server](https://msdn.microsoft.com/library/ms137731.aspx).  
  
 Per una panoramica di [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] e [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], vedere [Integration Services &#40;SSIS&#41; e strumenti di gestione](https://msdn.microsoft.com/library/ms140028.aspx)%20and%20Studio%20Environments.md).  
  
## Progetti di Integration Services che contengono pacchetti  
 Un progetto è un contenitore in cui si sviluppano pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
 In un progetto di [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] vengono archiviati e raggruppati i file correlati al pacchetto. Ad esempio, in un progetto sono inclusi i file necessari per creare una specifica soluzione di estrazione, trasferimento e caricamento specifica (ETL).  
  
 Prima di creare un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], è necessario acquisire dimestichezza con il contenuto di base di questo tipo di progetto. Una volta compreso il contenuto, è possibile cominciare a creare e utilizzare un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## Cartelle dei progetti di Integration Services  
 Nel diagramma seguente vengono illustrate le cartelle di un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 ![Cartelle di un progetto di Integration Services](../integration-services/media/solutionexplorer.gif "Cartelle di un progetto di Integration Services")  
  
 Nella tabella seguente si descrivono le cartelle incluse in un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
|Cartella|Description|  
|------------|-----------------|  
|[!INCLUDE[ssIS](../includes/ssis-md.md)] Pacchetti|Contiene i pacchetti. Per altre informazioni, vedere [Pacchetti di Integration Services &#40;SSIS&#41;](../integration-services/integration-services-ssis-packages.md).|  
|Varie|Sono contenuti file diversi dai file di pacchetto.|  
  
## File dei progetti di Integration Services  
 Quando si aggiunge un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] nuovo o esistente a una soluzione, tramite [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] vengono creati file di progetto con estensione dtproj, dtproj.user e database.  
  
-   Nel file con estensione dtproj sono contenute informazioni sulle configurazioni del progetto e su elementi quali i pacchetti.  
  
-   Il file con estensione dtproj.user contiene informazioni relative alle preferenze dell'utente per l'utilizzo del progetto.  
  
-   Nel file con estensione database sono contenute le informazioni necessarie a [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## Specifica delle versioni di destinazione nei progetti di Integration Services  
 In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] è possibile creare, gestire ed eseguire pacchetti destinati a SQL Server 2016, SQL Server 2014 o SQL Server 2012.  
  
 In Esplora soluzioni fare clic con il pulsante destro del mouse su un progetto di Integration Services e scegliere **Proprietà** per aprire le pagine delle proprietà per il progetto. Nella scheda **Generale** di **Proprietà di configurazione**selezionare la proprietà **TargetServerVersion** , quindi scegliere SQL Server 2016, SQL Server 2014 o SQL Server 2012.  
  
 ![TargetServerVersion property in project properties dialog box](../integration-services/media/targetserverversion2.png "TargetServerVersion property in project properties dialog box")  
  
## Soluzioni che contengono progetti  
 Una soluzione è un contenitore tramite cui vengono raggruppati e gestiti i progetti utilizzati durante lo sviluppo di soluzioni aziendali end-to-end. Una soluzione consente di gestire più progetti come una singola unità e raggruppa uno o più progetti correlati che concorrono a formare una soluzione aziendale.  
  
 Nelle soluzioni possono essere inclusi diversi tipi di progetto. Per creare un pacchetto di [!INCLUDE[ssIS](../includes/ssis-md.md)] mediante Progettazione [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], sarà necessario utilizzare un progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in una soluzione fornita da [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
 Quando si crea una nuova soluzione, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] aggiunge una cartella specifica della soluzione a Esplora soluzioni e crea file con estensioni sln e suo:  
  
-   Il file con estensione sln contiene informazioni sulla configurazione della soluzione e un elenco dei progetti della soluzione.  
  
-   Il file con estensione suo contiene informazioni sulle preferenze dell'utente relative alla soluzione.  
  
 Quando si crea un nuovo progetto in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], viene automaticamente creata una soluzione, ma è anche possibile creare una soluzione vuota a cui aggiungere progetti in un secondo tempo.  
  
> **NOTA:** per impostazione predefinita, quando si crea un nuovo progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], la soluzione non viene visualizzata nel riquadro **Esplora progetti**. Per modificare questo comportamento predefinito, scegliere **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni** e quindi fare clic su **Generale**. Nella pagina **Generale** selezionare **Mostra sempre soluzione**.  
  
## Attività correlate  
 [Aggiunta o rimozione di un progetto di Integration Services da una soluzione](../Topic/Add%20or%20Remove%20an%20Integration%20Services%20Project%20in%20a%20Solution.md)  
  
 [Creazione di un nuovo progetto di Integration Services](../Topic/Create%20a%20New%20Integration%20Services%20Project.md)  
  
 [Aggiunta di un elemento a un progetto di Integration Services](../Topic/Add%20an%20Item%20to%20an%20Integration%20Services%20Project.md)  
  
 [Copia di elementi di progetto](../Topic/Copy%20Project%20Items.md)  
  
## Contenuto correlato  
 [Sviluppo di un progetto di Integration Services](../Topic/Development%20of%20an%20Integration%20Services%20Project.md)  
  
  