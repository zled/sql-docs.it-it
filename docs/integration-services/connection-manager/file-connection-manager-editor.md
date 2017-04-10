---
title: "Editor gestione connessione file | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.fileconnectionmanager.f1"
helpviewer_keywords: 
  - "Editor gestione connessione file"
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# Editor gestione connessione file
  Utilizzare la finestra di dialogo **Editor gestione connessione file** per specificare le proprietà utilizzate per la connessione a un file o a una cartella.  
  
> [!NOTE]  
>  È possibile impostare la proprietà ConnectionString per la gestione connessione file specificando un'espressione nella finestra Proprietà di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Tuttavia, per evitare un errore di convalida quando si usa un'espressione per specificare il file o la cartella, aggiungere il percorso di un file o di una cartella in **Editor gestione connessione file** per **File/Cartella**.  
  
 Per ulteriori informazioni sulla gestione connessione file, vedere [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md).  
  
## Opzioni  
 **Tipo di utilizzo**  
 Consente di specificare se **Gestione connessione file flat** deve connettersi a un file o a una cartella esistente o creare un nuovo file o cartella.  
  
|Valore|Description|  
|-----------|-----------------|  
|Creazione file|Consente di creare un nuovo file in fase di esecuzione.|  
|File esistente|Consente di utilizzare un file esistente.|  
|Creazione cartella|Consente di creare una nuova cartella in fase di esecuzione.|  
|Cartella esistente|Consente di utilizzare una cartella esistente.|  
  
 **File/Cartella**  
 Se si sceglie **File**, specificare il file da usare.  
  
 Se si sceglie **Cartella**, specificare la cartella da utilizzare.  
  
 **Sfoglia**  
 Selezionare il file o la cartella usando la finestra di dialogo **Seleziona file** o **Sfoglia cartella**.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)  
  
  