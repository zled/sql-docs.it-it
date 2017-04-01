---
title: "Connessione a un database di Access | Microsoft Docs"
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
  - "Access [Integration Services]"
  - "database di Access [Integration Services]"
ms.assetid: 229fbd46-ef6a-4609-a4cc-d80d52c33cf1
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Connessione a un database di Access
  Per connettere un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] a un'origine dati di Microsoft Office Access, è necessario disporre di una gestione connessione e di un provider di dati OLE DB. Il provider di dati usato dipende dalla versione di Access in cui è stata creata l'origine dati:  
  
-   Per Access 2003 e versioni precedenti, il pacchetto richiede il provider OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet.  
  
-   Per Access 2007, il pacchetto richiede il provider OLE DB per il motore di database di Microsoft Office 12.0 Access.  
  
 È possibile creare una gestione connessione OLE DB e selezionare il provider di dati corrispondente dall'area Gestioni connessioni di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o dall'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  In un computer a 64 bit è necessario eseguire i pacchetti che si connettono a origini dati di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access in modalità a 32 bit. Il provider OLE DB [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet e il provider OLE DB per il motore di database di Microsoft Office 12.0 Access sono disponibili solo nelle versioni a 32 bit.  
  
## Connessione a un'origine dati in formato Access 2003 o precedente  
  
#### Per creare una gestione connessione Access dall'area Gestioni connessioni  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il pacchetto.  
  
2.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'area **Gestioni connessioni** e quindi scegliere **Nuova connessione OLE DB**.  
  
3.  Nella finestra di dialogo **Configura gestione connessione OLE DB** fare clic su **Nuova**.  
  
     Per altre informazioni, vedere [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
4.  Nella finestra di dialogo **Gestione connessione** selezionare **Provider OLE DB di Microsoft Jet 4.0** per **Provider** e quindi configurare la gestione connessione in base alle proprie esigenze.  
  
#### Per creare una connessione ad Access dall'Importazione/Esportazione guidata SQL Server  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] avviare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Nella pagina **Scelta origine dati** selezionare **Microsoft Access** per **Origine dati** e quindi configurare la connessione ad Access.  
  
     Quando si seleziona **Microsoft Access** come **Origine dati**, la procedura guidata crea automaticamente la gestione connessione OLE DB necessaria con il provider di dati corretto. Per altre informazioni, vedere [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
## Connessione a un'origine dati in formato Access 2007  
 Per accedere a un'origine dati di Access 2007, la gestione connessione OLE DB richiede il provider OLE DB per il motore di database di Microsoft Office 12.0 Access. Questo provider viene installato automaticamente con [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office System 2007. Se Office System 2007 non è installato nel computer in cui è in esecuzione [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], è necessario installare il provider separatamente. Per installare il provider OLE DB per il motore di database di Microsoft Office 12.0 Access, scaricare e installare i componenti disponibili nella pagina Web [Driver di Office System 2007: Data Connectivity Components](http://go.microsoft.com/fwlink/?LinkId=98155).  
  
#### Per creare una gestione connessione OLE DB dall'area Gestioni connessioni  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aprire il pacchetto.  
  
2.  Fare clic con il pulsante destro del mouse in un punto qualsiasi dell'area **Gestioni connessioni** e quindi scegliere **Nuova connessione OLE DB**.  
  
3.  Nella finestra di dialogo **Configura gestione connessione OLE DB** fare clic su **Nuova**.  
  
     Per altre informazioni, vedere [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
4.  Nella finestra di dialogo **Gestione connessione** selezionare **Provider OLE DB per il motore di database di Microsoft Office 12.0 Access** per **Provider** e quindi configurare la gestione connessione in base alle proprie esigenze.  
  
    > [!NOTE]  
    >  Per stabilire una connessione a un'origine dati che usa Access 2007, non è possibile selezionare **Provider OLE DB di Microsoft Jet 4.0** come **Origine dati**.  
  
#### Per creare una connessione OLE DB dall'Importazione/Esportazione guidata SQL Server  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] avviare l'Importazione/Esportazione guidata [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  Nella pagina **Scelta origine dati** selezionare **Provider OLE DB per il motore di database di Microsoft Office 12.0 Access** per **Origine dati** e quindi configurare la connessione in base alle proprie esigenze.  
  
    > [!NOTE]  
    >  Per stabilire una connessione a un'origine dati che usa Access 2007, non è possibile selezionare **Provider OLE DB di Microsoft Jet 4.0** come **Origine dati**.  
  
     Quando si seleziona **Provider OLE DB per il motore di database di Microsoft Office 12.0 Access** come **Origine dati**, la procedura guidata crea automaticamente la gestione connessione OLE DB necessaria con il provider di dati corretto. Per altre informazioni, vedere [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
## Vedere anche  
 [Connessione a una cartella di lavoro di Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md)  
  
  