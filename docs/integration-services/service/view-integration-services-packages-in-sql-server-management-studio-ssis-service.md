---
title: "Visualizzare pacchetti di Integration Services in SQL Server Management Studio (servizio SSIS) | Microsoft Docs"
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
  - "visualizzazione di pacchetti"
  - "connessioni [Integration Services], pacchetti"
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# Visualizzare pacchetti di Integration Services in SQL Server Management Studio (servizio SSIS)
    
> [!IMPORTANT]  
>  In questo argomento viene illustrato il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , un servizio Windows per la gestione dei pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] supporta il servizio per la compatibilità con le versioni precedenti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. A partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], è possibile gestire oggetti come i pacchetti del server Integration Services.  
  
 In questo argomento viene descritta la procedura per la connessione a [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e la visualizzazione di un elenco dei pacchetti gestiti dal servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
### Per connettersi a Integration Services  
  
1.  Fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server**, quindi **SQL Server Management Studio**.  
  
2.  Nella finestra di dialogo **Connetti al server** selezionare **Integration Services** dall'elenco **Tipo server**, specificare il nome del server nella finestra di dialogo **Nome server**e quindi fare clic su **Connetti**.  
  
    > [!IMPORTANT]  
    >  Se non è possibile stabilire la connessione con [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è probabile che il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] non sia in esecuzione. Per informazioni sullo stato del servizio, fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Microsoft SQL Server**, **Strumenti di configurazione**, quindi fare clic su **Gestione configurazione SQL Server**. Nel riquadro di sinistra fare clic su **Servizi di SQL Server**. Nel riquadro di destra cercare il servizio [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Se non è già in esecuzione, avviare il servizio.  
  
     [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] si apre. Per impostazione predefinita, la finestra Esplora oggetti viene aperta e posizionata nell'angolo inferiore sinistro del programma. Se Esplora oggetti non viene visualizzato, scegliere **Esplora oggetti** dal menu **Visualizza**.  
  
### Per visualizzare i pacchetti gestiti da Integration Services  
  
1.  In Esplora oggetti espandere la cartella Pacchetti archiviati.  
  
2.  Espandere le sottocartelle di Pacchetti archiviati per visualizzare i pacchetti.  
  
## Vedere anche  
 [Gestione dei pacchetti &#40;servizio SSIS&#41;](../../integration-services/service/package-management-ssis-service.md)   
 [Utilizzo di SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
  
  