---
title: "Editor destinazione SQL Server (pagina Avanzate) | Microsoft Docs"
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
  - "sql13.dts.designer.sqlserverdestadapter.advanced.f1"
helpviewer_keywords: 
  - "Editor destinazione SQL Server"
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# Editor destinazione SQL Server (pagina Avanzate)
  Usare la pagina **Avanzate** della finestra di dialogo **Editor destinazione SQL** per specificare le opzioni di inserimento bulk avanzate.  
  
 Per ulteriori informazioni sulla destinazione SQL Server, vedere [SQL Server Destination](../../integration-services/data-flow/sql-server-destination.md).  
  
## Opzioni  
 **Mantieni valori Identity**  
 Consente di specificare se l'attività deve inserire valori nelle colonne Identity. Il valore predefinito di questa proprietà è **False**.  
  
 **Mantieni valori Null**  
 Consente di specificare se l'attività deve mantenere i valori Null. Il valore predefinito di questa proprietà è **False**.  
  
 **Blocco a livello di tabella**  
 Consente di specificare se la tabella viene bloccata durante il caricamento dei dati. Il valore predefinito di questa proprietà è **True**.  
  
 **Vincoli CHECK**  
 Consente di specificare se l'attività deve verificare i vincoli. Il valore predefinito di questa proprietà è **True**.  
  
 **Attive trigger**  
 Consente di specificare se l'inserimento bulk deve attivare i trigger nelle tabelle. Il valore predefinito di questa proprietà è **False**.  
  
 **Prima riga**  
 Consente di specificare la prima riga da inserire. Il valore predefinito della proprietà è **-1**, a indicare che non è stato assegnato alcun valore.  
  
> [!NOTE]  
>  Deselezionare la casella in **Editor destinazione SQL** per indicare che non si vuole assegnare alcun valore alla proprietà. Usare -1 nella finestra **Proprietà**, in **Editor avanzato** e nel modello a oggetti.  
  
 **Ultima riga**  
 Consente di specificare l'ultima riga da inserire. Il valore predefinito della proprietà è **-1**, a indicare che non è stato assegnato alcun valore.  
  
> [!NOTE]  
>  Deselezionare la casella in **Editor destinazione SQL** per indicare che non si vuole assegnare alcun valore alla proprietà. Usare -1 nella finestra **Proprietà**, in **Editor avanzato** e nel modello a oggetti.  
  
 **Numero massimo di errori**  
 Consente di specificare il numero massimo di errori che possono verificarsi prima dell'arresto dell'inserimento bulk. Il valore predefinito della proprietà è **-1**, a indicare che non è stato assegnato alcun valore.  
  
> [!NOTE]  
>  Deselezionare la casella in **Editor destinazione SQL** per indicare che non si vuole assegnare alcun valore alla proprietà. Usare -1 nella finestra **Proprietà**, in **Editor avanzato** e nel modello a oggetti.  
  
 **Timeout**  
 Consente di specificare il numero di secondi di attesa prima che l'inserimento bulk venga arrestato a causa di un timeout.  
  
 **Colonne di ordinamento**  
 Consente di digitare i nomi delle colonne di ordinamento. È possibile ordinare ogni colonna in ordine crescente o decrescente. Se si utilizzando più colonne di ordinamento, delimitare l'elenco con virgole.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor destinazione SQL &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/sql-destination-editor-connection-manager-page.md)   
 [Editor destinazione SQL &#40;pagina Mapping&#41;](../../integration-services/data-flow/sql-destination-editor-mappings-page.md)   
 [Caricamento bulk dei dati tramite la destinazione SQL Server](../../integration-services/data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  