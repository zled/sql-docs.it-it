---
title: "Editor destinazione SQL Server (pagina Gestione connessione) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sqlserverdestadapter.connection.f1"
helpviewer_keywords: 
  - "Editor destinazione SQL Server"
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# Editor destinazione SQL Server (pagina Gestione connessione)
  Usare la pagina **Gestione connessione** della finestra di dialogo **Editor destinazione SQL** per specificare le informazioni sull'origine dei dati e visualizzare un'anteprima dei risultati. La destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] carica i dati in tabelle o viste di un database di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Per ulteriori informazioni sulla destinazione SQL Server, vedere [SQL Server Destination](../../integration-services/data-flow/sql-server-destination.md).  
  
## Opzioni  
 **gestione connessione OLE DB**  
 Selezionare una connessione esistente nell'elenco oppure fare clic su **Nuova** per creare una nuova connessione.  
  
 **Nuova**  
 Consente di creare una nuova connessione usando la finestra di dialogo **Configura gestione connessione OLE DB**.  
  
 **Tabella o vista**  
 Consente di selezionare una tabella o vista esistente nell'elenco oppure di creare una nuova connessione facendo clic su **Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova tabella usando la finestra di dialogo **Crea tabella**.  
  
> [!NOTE]  
>  Quando si fa clic su **Nuova**, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] genera un'istruzione CREATE TABLE predefinita basata sull'origine dati connessa. Questa istruzione CREATE TABLE predefinita non includerà l'attributo FILESTREAM anche se la tabella di origine include una colonna con l'attributo FILESTREAM dichiarato. Per eseguire un componente [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] con l'attributo FILESTREAM, implementare innanzitutto l'archiviazione di FILESTREAM nel database di destinazione. Aggiungere quindi l'attributo FILESTREAM all'istruzione CREATE TABLE nella finestra di dialogo **Crea tabella**. Per altre informazioni, vedere [Dati BLOB &#40;Binary Large Object&#41; &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Anteprima**  
 Consente di visualizzare in anteprima i risultati nella finestra di dialogo **Anteprima risultati query**. L'anteprima supporta la visualizzazione di un massimo di 200 righe.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor destinazione SQL &#40;pagina Mapping&#41;](../../integration-services/data-flow/sql-destination-editor-mappings-page.md)   
 [Editor destinazione SQL &#40;pagina Avanzate&#41;](../../integration-services/data-flow/sql-destination-editor-advanced-page.md)   
 [Caricamento bulk dei dati tramite la destinazione SQL Server](../../integration-services/data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  