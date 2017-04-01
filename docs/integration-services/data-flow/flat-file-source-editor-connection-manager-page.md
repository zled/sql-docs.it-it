---
title: "Editor origine file flat (pagina Gestione connessione) | Microsoft Docs"
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
  - "sql13.dts.designer.flatfilesourceadapter.connection.f1"
helpviewer_keywords: 
  - "Editor origine file flat"
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
caps.latest.revision: 29
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 29
---
# Editor origine file flat (pagina Gestione connessione)
  Utilizzare la pagina **Gestione connessione** della finestra di dialogo **Editor origine file flat** per selezionare la gestione connessione file flat per l'origine da utilizzare. L'origine file flat legge i dati da un file di testo. I dati possono essere in formato delimitato, a larghezza fissa o misto.  
  
 Un'origine file flat può utilizzare uno dei tipi seguenti di gestione connessione:  
  
-   Gestione connessione file flat se l'origine è un singolo file flat. Per ulteriori informazioni, vedere [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md).  
  
-   Gestione connessione per più file flat se l'origine è data da più file flat e l'attività Flusso di dati si trova in un contenitore Ciclo, ad esempio il contenitore Ciclo For. In ogni ciclo del contenitore, l'origine file flat carica dati dal nome file successivo fornito dalla gestione connessione per più file. Per ulteriori informazioni, vedere [Multiple Flat Files Connection Manager](../../integration-services/connection-manager/multiple-flat-files-connection-manager.md).  
  
 Per ulteriori informazioni sull'origine file flat, vedere [Flat File Source](../../integration-services/data-flow/flat-file-source.md).  
  
## Opzioni  
 **Gestione connessione file flat**  
 Consente di selezionare una gestione connessione esistente nell'elenco o di creare una nuova gestione connessione facendo clic su **Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova gestione connessione usando la finestra di dialogo **Editor gestione connessione file flat**.  
  
 **Mantieni i valori Null dell'origine come valori Null nel flusso di dati**  
 Consente di specificare se mantenere i valori Null durante l'estrazione dei dati. Il valore predefinito della proprietà è **false**. Quando questo valore è f**alse**, l'origine del file flat sostituisce i valori Null dai dati di origine con i valori predefiniti corretti per ogni colonna, ad esempio stringhe vuote per colonne con stringhe e zero per colonne numeriche.  
  
 **Anteprima**  
 Consente di visualizzare in anteprima i risultati nella finestra di dialogo **Vista dati**. L'anteprima supporta la visualizzazione di un massimo di 200 righe.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor origine file flat &#40;pagina Colonne&#41;](../../integration-services/data-flow/flat-file-source-editor-columns-page.md)   
 [Editor origine file flat &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/flat-file-source-editor-error-output-page.md)   
 [Gestione connessione file flat](../../integration-services/connection-manager/flat-file-connection-manager.md)  
  
  